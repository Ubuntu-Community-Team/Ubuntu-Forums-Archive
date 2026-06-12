---
title: "MVC pattern in PHP"
date: 2008-05-05
forum: Programming Talk
---

### Post by Waves77 on 2008-05-05
I'm trying to teach myself some more programming skills for my PHP experiments - I have a few questions about the MVC pattern in a LAMP type of setting.

Say I have an address book:
- Model: this would be the SQL tables where all the addresses are stored, right?
- Controller: the functions/methods that update/change the addresses.
- View: A template (HTML or Smarty) to display the variables and layout into the browser.

My questions are:
- The functions that retrieve the information for display, should that be part of the controller, or the view?
- Say I update an address, the logic for this would be in the controller, but how should I pass the information from the view to the controller? Me guess is import the controller function/class into the php script, and upon submission of the html form (view) it calls the method the processes the form variables, and updates the model (database) where needed. Am I getting this right?
- For a larger application, I think I would go from sql to xml and from xml to a smarty array - does this make sense for larger applications? The xml to smarty functionality, should that be part of the view/templates or should it be part of the controller?

Thanks for any help! :grin:

---

### Post by RIchard James13 on 2008-05-05
Based on my highly OPINIONATED view of MVC

> - The functions that retrieve the information for display, should that be part of the controller, or the view?

It should be part of all three. One part is based on the Model and extracts the data using SQL. Another part is in the View that takes that part from the Model and displays it. The other part is in the Controller that tells the View to take the data from the Model.

If however the data is not static then sometimes the View may need to update it's data from the Model without any input from the Controller. Whether you agree with that depends on whether you see the Controller as a strict interface between the system and the user or as an overarching piece of software that handles every update from the Model to the View.

Does the Controller only act when the user permits it? Or is it autonomous and can work without user intervention?

> Say I update an address, the logic for this would be in the controller, but how should I pass the information from the view to the controller? Me guess is import the controller function/class into the php script, and upon submission of the html form (view) it calls the method the processes the form variables, and updates the model (database) where needed. Am I getting this right?

The View is normally considered output only, all input goes into the Controller. But in reality that might not always work. Instead you might want to consider those parts of the View that input information as part of the Controller instead. In other words if you find your code is not following the pattern because the View seems to be doing the Controllers job then maybe that is not actually the View after all.

I can't answer your last question as I don't know enough about a smarty array.

Also consider that MVC is a way to separate functionality so that changes in one do not affect another. Thus if when making decisions about what goes into which section ask yourself if the Model, View or Controller is changed later does my current decision about what goes where make it so that I have to change 1, 2 or 3 parts? For instance if you decide that you are going to switch from one data storage type to another, that decision should only affect the Model, not the View or Controller. If it does affect one of those two then you have not properly separated the Model from the rest of the code.

What I have said is not Gospel it is my opinion.

---

### Post by Waves77 on 2008-05-07
Thanks, your explanation clarified my doubts. The updates would only be triggered by the user, so that's a lot easier.

The way I'm dividing this up now is:

MODEL: 
- MySQL database itself
- SQL queries functions
- SQL results to XML

VIEW: 
- Smarty templates (plus any javascript etc.)
- XML to Smarty variables*
- Smarty variables to XML (so I can pass it cleanly to the controller)

CONTROLLER:
- All the business logic, responding to user interaction, and      triggering changes in model and view.   
      

* These look like this: [http://www.smarty.net/crashcourse.php](http://www.smarty.net/crashcourse.php)

Thanks again :)

---

