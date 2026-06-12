---
title: "program (game) not working, trying to learn diagnostics (11.10, Lenovo T500)"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by Jmob on 2011-12-28
So, I've got a game (Aquaria, from the really cool Humble Indie Bundle program, check it out).  It's just a game, and even one I've played before in Windows, so I don't really care terribly about it.  But I loaded it up from a downloaded .deb file to see how it would run in Ubuntu.

Ran just once, and it seemed to work just fine.  Now, it won't run at all.  Triggering the program from the Unity interface brings up the icon momentarily, and then it goes away.  No big deal, but I thought this might be a good way to learn how to diagnose things in Ubuntu (esp with Unity).  I'm realizing there's some big gaps in my knowledge, though.

Tried deleting the configuration folder (.Aquaria) in my home directory.  No change.  Reinstalled with the .deb file again.  Nothing.  I would have run the thing from the terminal, see whether, but now that I'm in Unity I'm a bit lost as to where I even find the command itself (I knew this much, at least, in GNOME).  But that's only the first step.

So, in short, what's the process for diagnosing something that doesn't run in Ubuntu?  Running it in the terminal, perhaps, identifying missing packages?  Why would something run once and then not again?  

Again, I care little about this specific program, but I'd like to use it so that I don't have to take a ton of time when something important comes along.  So I'm more interested in general approaches.  Thanks everyone.

---

### Post by mastablasta on 2011-12-28
> **Jmob said:**
> 
So, in short, what's the process for diagnosing something that doesn't run in Ubuntu?  Running it in the terminal, perhaps, identifying missing packages?  Why would something run once and then not again?  
.
it could be just missing a package. especially if it was made for gnome 2 or something like that.

run it in terminal and it should give you any error messages.

Unity could interfere with programmes.

---

### Post by thatguruguy on 2011-12-28
> **mastablasta said:**
> 
Unity could interfere with programmes.

That seems unlikely. In fact, it borders on FUD. Please don't just make stuff up.  EDIT: In fact, I just opened Aquaria in Unity. No problems here, so Unity seems an unlikely culprit.

To the OP: does Aquaria show up in the Dash when you search for it?  If so, we're going to go through a couple steps to figure out where the executable is, so you can run it from the command line.

---

### Post by anewguy on 2011-12-28
To open a terminal window in Unity:

- click on the top-most button on the Unity menu - "Dash Home"

- in the search string put in ter

- click on the terminal icon


Now try running your program from the command line.  This is a good place to start as you will see any warnings or error messages that you wouldn't see trying to run it as a normal windowed application.

Copy/paste that window back here and we'll take a look at things and perhaps suggest a next step for you.

Dave ;)

---

### Post by Jmob on 2011-12-30
Shows up in the Dash, yes.  Clicking it brings up an icon on the sidebar, there for a sec or two, then disappears.

Obvious guesses in the Terminal (Aquaria, aquaria) don't seem to do anything, so it's not that, or it's not in the path, one way or another.

---

### Post by anewguy on 2011-12-30
Hold the mouse button down and drag the icon for your app from the menu to your desktop.  Once it is on your desktop, right mouse click on it, select "Properties" and select the "Basic" tab - it is probably the default.  The third entry on that screen - "Command:" - is what you would type in the terminal command line to run your app.  Running from the command line should show any messages in the terminal window.

Dave ;)

---

### Post by Jmob on 2011-12-30
Thanks Dave.  Worked just fine, though I'm surprised it takes that kind of process to get the info.  With zero apparent right click functionality in the dash, you'd think something of this sort would be an obvious choice.

Anyway, here's what I got in response

command: /opt/Aquaria/aquaria

Response:
> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13

---

### Post by Jmob on 2011-12-30
I'm over my current understanding right now, but I'm gathering that this is an openGL issue.  Notably, I've also got FGLRX currently installed; is that a concern?

Edit:  These codes seem to relate to this, supporting the FGLRX theory, but I've not found a general index of what they mean:
[http://askubuntu.com/questions/77636/getting-compiz-to-work-with-ubuntu-11-10-and-fglrx](http://askubuntu.com/questions/77636/getting-compiz-to-work-with-ubuntu-11-10-and-fglrx)

---

### Post by anewguy on 2011-12-30
Judging from that link it would appear you need to install the open source ATI driver.  So, if the flgrx driver you are using is from the repositories, I would (in a terminal window again):

sudo apt-get remove flgrx <press enter>

sudo apt-get install fglrx <press enter>

and see what happens.


You might also need to be sure that glx has direct rendering working:

glxinfo | grep direct <press enter>



Dave ;)

---

### Post by Jmob on 2011-12-30
I'll try this, thanks.  

Since the point here is for me to learn rather than to just get this working, some questions:

removing and then installing fglrx (the same thing?) per the instructions above.  How does that move me from the proprietary driver (installed originally through the "additional drivers" application)  to the open source driver (presumably the default one I already replaced?).  Or am I misconstruing this?

Also, glxinfo appears to be not installed, terminal requesting mesa-utils be installed first.  No problem, but is the fact that this is missing a notable phenomenon?

---

### Post by anewguy on 2011-12-30
Hummmm......so glxinfo on its' own does nothing?

As far as the open source driver - I'll need to look.  I thought the one in the repository was it, but it might actually have another name.

Dave ;)

---

### Post by Jmob on 2011-12-31
I thought flgrx was the closed-source ATI one.  I'll look, too.

Also, what exactly does "remove flgrx" followed by "install flgrx" do?  I must not be understanding something, as that looks like a full circle to me.

And, thanks again.

---

### Post by anewguy on 2012-01-01
It basically removes it so you can do a clean reinstall of it.

---

### Post by anewguy on 2012-01-01
Looks like the open source ATI driver will be Radeon or ATI.  Try following this link:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

