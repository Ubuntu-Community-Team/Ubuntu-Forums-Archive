---
title: "Python Session Handling"
date: 2008-07-14
forum: Programming Talk
---

### Post by themusicwave on 2008-07-14
Hey Everyone,

So I am working on a personal website for my wedding trying to get all our guests to RSVP online and such.  

For the site I want to do some account creation and allow users to login and view stuff as well as RSVP.

I am primarily a desktop progammer, but I am certain I can pul this off.  I already have the form working for the RSVP, it is just that no one can get to the information yet due to the lack of login.

My plan is to have user's create an account and store this in my POstgres database, that part is done.  

My only snag is that I really don't now how to do sessions in Python.  I know PHP has the $SESSION variable, which I used last time I made a website.   This time I want to do it in Python, because I prefer it and also just to learn.

I understand the basic concept, I need to generate a unique ID for each user when they first login.  From there I need to continue to pass that ID as they move from page to page.  MY only questions is how to pass it.

I was thinking of using a hidden form element, and he post method.  My primary question is how do I pass around this information even if a page doesn't have a submit button?  I could use a Cookie, but would rather not.  I would rather do it with POST.

Thanks,

Jon

---

### Post by pmasiar on 2008-07-14
Unique userID is completely separate from session ID: whole point of sessionID is it should be impossible to guess. UserID of the session could be stored as variable in session object.

I did very simple thing: Get really random string [Recipe/65110 recipe from Python Cookbook](http://aspn.activestate.com/ASPN/Cookbook/Python/) and use it as sessionID == filename in .sessions directory to save (pickle) dictionary with session-related variables. Application always returns sessionID you assigned to it on login. If file exists, unpickle it - voila here are all vars from last time! :-) Of course including Userid: otherwise users can subvert your login, pass you userid of someone else! You can never trust identification from the client.

---

### Post by themusicwave on 2008-07-14
Thanks for the recipe, I should be able to use it to generate the ID on login.

Here is my idea.

On login use the recipe to generate a session id.

Store this in a Sessions table, the table will have the userid(database primary key of the user table), the login time, last active time(last time they triggered a script), their ip and the session id.

Each time a script is run I check for the IP in the DB.  If it exists I open the session db to see who they are and update the last active time. 

Then if after X minutes they are still inactive.  A script running on the server that is checking for inactivity logs them out.

I could append the session ID to the url and validate it against their login IP each time.  This prevents someone else from pasting the url and becoming them.

Hows that sound?

---

### Post by pmasiar on 2008-07-14
Sounds good. You can use simpler faster database (dbm), or plain files, instead of connecting to DB, but do as you wish.

---

### Post by themusicwave on 2008-07-15
I think I'll stick with my postgres DB; I already have the code to connect to it done.  Also, much of the user information is already in the database.

Thanks again for the help pmasiar, I think all I really needed was that spark to get an idea going.  Now that I know how to create the unique session ID, I feel like the light bulb has gone off for everything else.

Perhaps I will post the code somewhere if it isn't too ugly and if anyone is interested.

Thanks again!

---

