---
title: "Any people with Python Flask web framework experience out there?"
date: 2020-05-15
forum: Programming Talk
---

### Post by mortalkorona on 2020-05-15
Any people with Python **Flask** web framework experience out there?
Especially with using **pytest** for **unit testing** and **functional testing.** I have some complicated questions in my luggage to unfold.

---

### Post by mIk3_08 on 2020-05-15
yes, mortalkorona. I'm not that expert on Flask but I have some python files here that will surely runs with Flask environment. which in fact, you can easily google it.

---

### Post by mortalkorona on 2020-05-15
Hi mlk, so I'm trying to learn and make pytest work for my Flask project by following this tutorial. I have managed to make PatKen's code work. But I wanted to refactor the [COLOR=#daa520]**Application Factory Function**[/COLOR] to use [COLOR=#8b4513]**Config class object**[/COLOR] instead of using this tutorial's [COLOR=#8b4513]**Config filename**[/COLOR] setup.

Do you know if switching from [COLOR=#8b4513]**Config filename**[/COLOR] to [COLOR=#8b4513]**Config class object**[/COLOR] in the [COLOR=#daa520]**Application Factory Function**[/COLOR] is known for causing issues when pytesting Flask?


**Testing a Flask Application using pytest**
[https://www.patricksoftwareblog.com/testing-a-flask-application-using-pytest/](https://www.patricksoftwareblog.com/testing-a-flask-application-using-pytest/)


**GitLab: flask_user_management_example**
[https://gitlab.com/patkennedy79/flask_user_management_example](https://gitlab.com/patkennedy79/flask_user_management_example)


**Instructions for bug fixing and setting up PatKen's example code:**
[PHP]
$ export FLASK_APP=main.py
$ flask run

# --- Error ---
# sqlalchemy.exc.OperationalError: (sqlite3.OperationalError) no such table: users

#_______________________________________________________________________________

$ flask db init

# --- Error ---
# directory = current_app.extensions['migrate'].directory
# KeyError: 'migrate


# --- Solution ---
# /project/__init__.py

from flask_migrate import Migrate # Was missing in example code.

    ..
    ..

def initialize_extensions(app):
    migrate = Migrate(app, db) # Was missing in example code.

    ..
    ..

#...............................................................................

$ flask db migrate -m "Users table."  
$ flask db upgrade 

#_______________________________________________________________________________

/flask_user_management_example$ pytest
/flask_user_management_example$ pytest tests

# --- Error ---

# ImportError while loading conftest '/flask_user_management_example/tests/conftest.py'.
# tests/conftest.py:2: in <module>
#   from project import create_app, db
#   E   ModuleNotFoundError: No module named 'project'


# --- Solution ---

# Move 'conftest.py' file from here:
/flask_user_management_example/tests/conftest.py

# To here:
/flask_user_management_example/conftest.py

# Run the tests, all 10 tests should display PASSED:
/flask_user_management_example$ pytest -v

[/PHP]

---

