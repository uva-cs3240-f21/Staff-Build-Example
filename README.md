# Staff-Build-Example
An example of the commands and settings needed to integrate a Django project with GitHub Actions (for continuous integration) and Heroku.

## Steps

Here's what I did to build this example:

1. Created my repo and cloned it locally.
2. Created a new .gitignore file with the appropriate Django things in the list (see example in this repo).
3. Created a new virtual environment by running `python -m venv ./venv` and then activating it.  For MacOS, this is `source ./venv/bin/activate`.  For Windows, it was `.\venv\Scripts\activate`.  See the python venv docs for more information.
4. Upgraded pip to get rid of the warning message (because why not...) with `python -m pip install --upgrade pip`.
5. Installed the libraries I needed with `pip`.  Once you have a `requirements.txt` file with your installs, you can do `pip install -r requirements.txt` and it will handle it for you.  (So that's what I did next... I created the `requirements.txt` file.)
6. Did all of the Django things I wanted to (created new project, new app, added a view, changed some urls, created a test, etc.).
7. Changed the `settings.py` file to handle issues with loading the `django_heroku` library.  It's not needed locally, so you can put it in a `try` statement.  See the file for the code.  There's some other changes in `settings.py` and other files marked with `SHERRIFF` for other common errors.  Search the repo to find them.
8. Added the `Profile` for Heroku so it knows how to `migrate` and how to launch our app.
9. After committing all this to GitHub, click on "Actions" in the menu beside "Code", "Issues", and "Pull Requests."  The first option in the upper left is to setup testing for Django with GitHub Actions.  __The only change you need to make is to ONLY test with one version of Python!__ After you click the button to setup testing, change the code on the left to __ONLY__ have Python 3.9.  Remove 3.7 and 3.8.  Then commit the file and watch the testing run!
10. Now over on Heroku, add a new app and connect your GitHub repo here on the "Deploy" page.  If you do not see your repo in the list (and more specifically, you don't see the class GitHub org), then you never accepted the invitation to join the org at the beginning of the semester.  You'll need to make a private post on Piazza to have this done again.
11. Under "Automatic deploys" on the "Deploy" page, make sure to turn this on and check the box for "Wait for CI to pass before deploy", which will make sure that it will only deploy if the GitHub Action succeeds.

And now your build process is set up!  Hooray!