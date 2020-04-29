# 14 Full Stack: Reverse Engineering Authentication

## Files Explanation

- server.js
    - In the server.js file the required npm packages and local files/routes are declared, the express app is created and configured, the port is set up on port 8080, passport is initialized,  Sequelize is synced with the database, and the server connection to the port is activated

- package.json
    - The project name is "1-Passport-Example" and the main file is server.js, which is the starting file for node.js
    - A nodemon package was installed so there is no need to restart the server at every change in the code
    - There are other npm packages that were installed and are listed as dependencies such as bcryptjs, express, express-session, mysql12, passport, passport-local, and sequelize

### Config

### Middleware

- isAuthenticated.js
    - Restricts routes that users cannot access until they've successfully logged in
    - If the user is logged in, it continues with request otherwise routes them to the login page.

- config.json
    - Connection configuration to connect to server to one of 3 databases, either development, testing, or production

- passport.js
    - Contains passport authentication middleware for node.js that authenticates users' log in requests with an email address and password
        - The "LocalStrategy" object  uses the functions to work with "strategy" from inside  of "passport-local" library 
        - The variable "db" reads the models that exist and that control my database
        - It uses the "validPassword" method to verify if the password is the same in the database
        - A new object is constructed to set how the user will sign in - by email
        - This email search will be done through sequelize the "findOne" method
        - If the user doesn't type the email, an error message will show: "Incorrect email"
        - The same with the password, a message will show: "Incorrect Password" if the input isn't correct

### Models

- index.js
    - Connects to database and imports users log in data
        - First index.js finds out what environment we are running in, and based on that it will configure Sequelize accordingly to the settings from config.json
        - After that it will use the FS library to read through the files found in the “models” folder that end with JS and is not itself, and then load them as models inside Sequelize
        - This is important because in the future we can add more models without changing the code, and just simply by adding more JS files into the "models" folder
        - Lastly the files takes in any associated models and associates them in the db

- user.js
    - Defines what data is stored in our database through creating a User model for Sequelize, which includes email and password both with data characteristics
        - Requires "bcrypt" for password hashing, which makes our database secure even if compromised
        - The file also provides the model access to the functions of "validPassword", which checks if an unhashed password entered by the user can be compared to the hashed password stored in our database, and "addHook" which automatically hashes their password prior to a User being created

### Public

- login.html
- member.html
- signup.html

### JS

- login.js
- members.js
- signup.js

### Stylesheets

- style.css

    - The "public" folder contains all the html pages: login, members, and signup and also contains the same matching files names in the "js" folder, which contains the javascript required for the html files
    - The JS files will wire the GET and POST calls to the proper API endpoints in the server to the proper buttons using jQuery after the DOM is loaded
    - The "stylesheet" folder contains the style.css file which only affects the margin of the signup and login forms

### Routes

- api-routes.js
    - This file contains POST and GET routes to sign in and sign out options for the user using the passport.authenticate middleware, sending the user to the "/members" page if they valid login credentials
    
- html-routes.js
    - This file contains the html routes that render the html pages: the authenticated ones for users that are logged in, or back to the login page otherwise

## Future Improvements for the Project

- Leveraging a previous application I've built, a secure password could be generated for the user automatically based on their input regarding types of characters and length when they sign up
- Another obvious improvement for the project comes in the form of styling, adding color, animations, borders, or a background would make the project more aesthetically pleasing

[Google Docs Link](https://docs.google.com/document/d/19q7guLBkYZZsbX0sc00ylG4t1nqxAddSiJCSRmWj2Ew/edit?usp=sharing)

[GitHub Project Repo](https://github.com/wtgibson/14-reverse-engineering-authentication)

## Author Links

![Site](images/william-gibson-jr-photo.jpg)

Will Gibson

[LinkedIn](https://www.linkedin.com/in/wtgibson/)

[GitHub](https://github.com/wtgibson)
