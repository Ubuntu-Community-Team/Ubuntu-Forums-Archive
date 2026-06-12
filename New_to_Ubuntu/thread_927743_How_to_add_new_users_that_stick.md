---
title: "How to add new users that stick"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by resander on 2008-09-23
I have only used Ubuntu for a short while running it as a single-user system. Now I want to add users, but the new users do not 'stick'.

Going to System->Administration->Users-and-Groups I can see two users: root and Ken Resander (my name - I installed Ubuntu from alternate distribution) with home directories /root and /home/ken respectively. I clicked on the root entry in the listbox, clicked the Unlock button and entered a password that made the 'Add user' button enabled, Clicking the latter brought up a dialog into which I entered new username, real name and password, but this dialog had no Apply/OK button so I had no way to save the new user. I do not know what I am doing wrong, so would be grateful for advice.

---

### Post by luckydeveloper on 2008-09-23
hey.. you did the right thing.. thats how you have to create/add users. you must see a "add" button. just click on it. thats it. your new user will be saved. 
then logout and give the username and password for that user. 

 if you prefer another login screen which shows the users like a list ....go to System -> Adminsistration -> login window -> local

---

### Post by resander on 2008-09-23
Thanks for the info, but it is still not working.

I have logged out-logged backin, switched user and rebooted, but for all these when trying to logon as a new user I keep getting 'invalid user/password. Also tried with several new users with same outcome.

Selecting System->Administration->Login Window and clicking Local tab brings up a list of desktop themes. Clicking the more likely tab 'Users' brings up an empty list of users.

I would have expected the new users to be listed in the home directory, but I can only see my /home/ken created by the installation script.

The last new-user I unsuccessfully tried was 'somebody' with password 'abcdefgh' (without the quotes). Can anyone make it stick?

---

### Post by digitalvectorz on 2008-09-23
Ken,

Instead of trying to go through GUI, try doing this:

Accessories > Terminal

```

prompt$ sudo adduser somebody

```

it should prompt you to enter a password, their real name, etc.

See if that sticks.

---

### Post by resander on 2008-09-23
Digitalvectorz,

Many thanks - it sticks!

So, is the answer to the topic question 'use the command line'?

I would have thought it is unlikely the GUI is not working. That should have been detected ages ago, so I am still curious to find out how to use  'Users and Groups' on the menu. Is there something odd with my install? If the GUI works for someone else maybe there is. Can anyone try adding a user and report if it works.

Any

---

### Post by Paqman on 2008-09-23
> **resander said:**
> 
So, is the answer to the topic question 'use the command line'?


No, the GUI should work fine. I do it all the time.

Can you post a screenshot of your "add user" window?

---

### Post by resander on 2008-09-23
Took a screenshot by the function in Accessories. Have never inserted screen shots before, so will just try to add a png image attachment file. If it comes out wrong or not at all, please let me know what I should have done.

---

### Post by terry_gardener on 2008-09-23
looks as though the screen resolution is set to low and the ok button is hiding below the bottom of the screen. 

try raising the screen resolution abit and then retry

---

### Post by Paqman on 2008-09-23
Alternatively, hold down alt and click-drag the window so you can reach the buttons.

---

### Post by resander on 2008-09-24
terry_gardener, Paqman,

Many thanks!

That's it - Ubuntu is excluding people with wonky eyes (I need to work at 640x480). It will not let me see the Cancel and OK buttons even at 800x600 screen resolution. I have used Windows a lot and this 'visible elements outside the screen' problem happened for some programs at 640x480, but it was rare. I have only just started with Ubuntu and stumbled upon this twice in 'set Screen Resolution' and in this one.

Maybe I cannot expect 640x480 to show all buttons etc in GUIs, but I do expect 800x600 to work. It does under Windows.

I think this ought to be brought to the attention of Ubuntu 'Central' (where?). The problem affects people with less than perfect vision and the steadily growing population of senior citizens that nowadays is computer literate.

---

### Post by andrewc6l on 2008-09-24
You can set up your desktop so it uses a larger virtual screen than the phyiscal screen. That might make Ubuntu a little easier to use for you.

Here is a thread going in the reverse direction (the user had a virtual screen and didn't want it):
[http://ubuntuforums.org/showthread.php?t=571638](http://ubuntuforums.org/showthread.php?t=571638)

---

### Post by Paqman on 2008-09-24
> **resander said:**
> 
I think this ought to be brought to the attention of Ubuntu 'Central' (where?). The problem affects people with less than perfect vision and the steadily growing population of senior citizens that nowadays is computer literate.

Agreed, accessibility is important.

The normal way to report bugs is through the [Launchpad](https://launchpad.net/ubuntu/+filebug) system. Not sure if this would be appropriate for an accessibility issue though? It's also not really an issue with Ubuntu itself, but i'm sure they'll pass the bug upstream.

Glad we've been able to fix your immediate problem, though. It's little tricks like alt to drag windows that nobody tells you about when you first switch to Linux!

---

### Post by lisati on 2008-09-24
> **Paqman said:**
> 
 It's little tricks like alt to drag windows that nobody tells you about when you first switch to Linux!

+1: and don't be scared to ask questions, on the whole we're a friendly bunch here. Sooner or later someone will come up with a suggestion of what to check or possible solutions.

---

### Post by DrMelon on 2008-09-24
Perhaps a magnifier program or plugin would help? Then you could have a high resolution and still see the things in close detail.

---

### Post by resander on 2008-09-24
Many thanks.

True, this is not an Ubuntu/Linux problem, it's just caused by application GUI-design. Most developers nowadays work at 1024x768 or higher resolutions and some may not be aware of the need for applications to work at lower resolutions. I have seen Windows GUI applications with the buttons below the screen at 640x480 with a lot of unused space at the bottom of visible area. In these cases the designers could have made their creations accessible for everyone by a few clicks in a GUI resource editor.

I think all Ubuntu applications should work at 800x600. Will contact Launchpad about this.

Again, many thanks.

---

