---
title: "Help getting started with RubyGTK"
date: 2010-01-30
forum: Programming Talk
---

### Post by dodgem on 2010-01-30
I've had some experience writing apps for work which are browser based, using ajax, ruby, and mysql.  However, i want to write something that does not depend on the browser and runs on the local machine (while still accessing the database on the server).

I had a look at xulrunner and i think i could slip into that pretty easily with my current knowledge, but i would really like to write the app in Ruby rather than xml and javascript.

The problem i've run into right from the start however is how to navigate the GUI.  I'm trying to use RubyGTK, and as a simple example, i have created a main window with a menu and statusbar.  Most of the menu is insensitive, apart from Exit and Login.  Clicking Login brings up a new window prompting for username and password, which then connects to the database and verifies the login.

Now the problem starts...  How do i reference the menu items to make them sensitive?  In a browser app i would do something like
```
mainmenu = document.getElementById('mainmenu')
for (menu in mainmenu){
  for (menuitem in mainmenu[menu]){
    if (mainmenu[menu][menuitem].getAttribute('inactive')){
      mainmenu[menu][menuitem].removeAttribute('inactive');
    }
    if (mainmenu[menu][menuitem].id == 'login'){
      mainmenu[menu][menuitem].setAttribute('inactive', true);
    }
  }
}

statusbar = document.getElementById('statusbar');
statusbar.firstChild.value = 'Logged in as ' + username;

```

In a RubyGTK app i presume i would hold all the menuitem objects in an array and pass the array to a method which sets or unsets the sensitivity, or better still, make the menu an object with a login and a logout method which iterates over its menuitems which would be objects held in instance variables?  Is it possible to navigate the gui as one would navigate an xml dom?

Am i thinking along the right lines here?  I get the feeling i need to completely shift my perspective to write a gui app in Ruby and GTK.  Do i need to get the hang of closures?  If someone could point me in the right direction preferably with an example i could follow i would be very grateful.  I feel at the moment like i'm in a dark room stumbling in no general direction.  I need to be told which direction the light switch is in!

Many thanks,
Simon

---

