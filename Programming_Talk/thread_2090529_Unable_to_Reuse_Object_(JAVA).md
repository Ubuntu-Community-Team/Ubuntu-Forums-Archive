---
title: "Unable to Reuse Object (JAVA)"
date: 2012-12-02
forum: Programming Talk
---

### Post by kevinharper on 2012-12-02
I have a login prompt.
Username & password checked on a DB.
DB returns the user's full name & access level.
If exactly one result, creates User(username, fullName, accessLevel) object.

I need to retrieve accessLevel from different panels that display components depending on it.

How do I get that same object's fullName and accessLevel from a new panel?

I am running into a catch22. I can create the object using the query results as soon as the user is authenticated.
```
IManageUser user = User(userName, fullName, accessLevel)
```
But my whole purpose of creating this user class is so I can access fullName & accessLevel from many different panels. But to instantiate it, I already have to know this information. Useless... There's gotta be an easier way, right?

I created an interface for the object but that only works within the panel that captured the username. It is captured from the textfield where the user entered it, at the login prompt.

How do I give EVERY panel access to that same information?

---

### Post by kevinharper on 2012-12-02
I thought about not creating a User object and just saving query results to some completely public variables. But in the future I may want to do more things, beyond saving/accessing three fields/vars.

Besides, not really sure how to do this either. Any help with this would also be greatly appreciated.

Thanks

---

### Post by KdotJ on 2012-12-02
Something you should perhaps look into is the [Singleton Pattern]("http://en.wikipedia.org/wiki/Singleton_pattern"). It basically allows a single object instance be used anywhere in an application... and it's always the same instance. 

For your problem, where you may have more than one user, you could have a UserStore class which is a singleton and has the users in it.

---

### Post by kevinharper on 2012-12-02
So it is only one user.
The person logs in and the program acts according to the user's access level.
In it's simplest form, my need is having global access to the username the user logged in with, and fullName & accessLevel which are returned by the database. At this point I am willing to pass on the user object just to get this to work and I can move on.

I saw a few posts about the singleton pattern but not the link you provided. I'll take a few minutes to read through it.

But given my essential need (the one I've posted a few lines above), do you think it applies?

---

### Post by KdotJ on 2012-12-02
The singleton sounds pretty much exactly what you want, it basically give global access to an object (in your case, your User object). Any other class in your application can access this user object and use its methods etc. 

What you could do, is initialise the singleton when the user logs in. Then any other part of your application could use the information for that user. 

Let's say your singleton is called User, the bits in your application code could be like:

```
String name = User.getInstance().getFullName();
```



The singleton pattern is sometimes criticised or introducing "global state" in an application... but you would be surprised how much this is used in the real world.

---

### Post by kevinharper on 2012-12-02
Yep... AWESOME. Looks like this is exactly what I need.

Once again, thank you!

---

### Post by KdotJ on 2012-12-02
No problem! Good luck with the application

---

### Post by kevinharper on 2012-12-02
Worked like a charm and was EXTREMELY easy to do.

Crazy thing is that I was very close to doing this just by trying to figure out how I could do it on my own. There are a couple of things though that mentally would have prevented me from ever getting to this solution/conclusion on my own. So yes... Thank you! This puts me at about 60% done w/ the project.

---

### Post by kevinharper on 2012-12-05
So it looks promising. :)

But I have reopened this issue because although the class the singleton User class is available to all other objects, the objects are pulling values as soon as the program starts... BEFORE the user logs in. This sets the values to "null" wherever I want dynamic content (based on User-class field values).

Values within the User class shouldn't get set until the user successfully logs in. What's the kosher way to do this?

---

### Post by kevinharper on 2012-12-05
I guess I should explain where I think the problem I'm having comes from...

Program starts with a CardLayout that switches through 3 panels (login, login error, login success).

Login success panel, in turn, contains another cardlayout (among other objects). So when the program starts, ALL of this is loaded at once. And because User doesn't get set until the user logs in, all JPanels testing the user's accessLevel get null values.

I'm guessing there is a way to not load "cards" until an event happens.

---

### Post by ofnuts on 2012-12-05
> **kevinharper said:**
> I guess I should explain where I think the problem I'm having comes from...

Program starts with a CardLayout that switches through 3 panels (login, login error, login success).

Login success panel, in turn, contains another cardlayout (among other objects). So when the program starts, ALL of this is loaded at once. And because User doesn't get set until the user logs in, all JPanels testing the user's accessLevel get null values.

I'm guessing there is a way to not load "cards" until an event happens.

You have to change your design to load the panels only once you know what they should contain based on user authentication data... or the panels can interpret unspecified values as "don't know, be ready for a change later" (for instance go invisible)

---

### Post by kevinharper on 2012-12-05
Done. It's a hack and I know it. But it works.

My LoginPanel controls what card to show in my CardLayoutPanel. I took the add & show statements out of the main class in CardLayoutpanel and placed in inside the public method that received LoginPanel String that controls viewed card.

A simple "if" stringReceived whatever.equal("success"), add successPanel to CardLayoutPanel and show it. WORKS EXACTLY LIKE I WANT IT TO! AWESOME!

Once again, thank you for your responses and for your help guys.

---

