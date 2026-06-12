---
title: "disable unity after enabling gnome-fallback"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by ben5 on 2014-10-24
I have enabled gnome-fallback but I am curious if I can remove the unity option to prevent people from logging into unity instead?

---

### Post by ajgreeny on 2014-10-24
In theory by removing the appropriate packages you can but why bother?  I don't know which you should remove, but be aware that even in my Xubuntu there two packages with "unity" in their name, both of which are necessary for other packages I want, so don't just accept everything that is removed when you and if you try this, check it all first so you don't also take packages you want to keep.

Why does it really matter if somebody else logs in to a unity desktop?  Make sure you don't tell them your password and they will only be able to login under another user which you can set up, and that will not affect you in any way.

---

### Post by ben5 on 2014-10-24
To explain these PC's are in a call center where we conduct phone interviews.  The PC's are old and slow.  Unity lags horribly.  The employees who use these PC's apparently decided to switch to Unity.  But this means it will be slower for them and the next person who logs in who likely doesn't even realize there are different desktops to choose from.   

Granted they mostly just connect to the server via ssh where questions are displayed on the screen that they read and they key in numerical codes for answers.  So the slowness of Unity is not a huge issue.  But sometimes the interviews are in a web broswer which will lag worse. 

Point is these are employees that I don't want to have the ability to log into unity and possibly cause slowness... They should log into the gnome fallback and access the survey they are assigned to only.

---

### Post by deadflowr on 2014-10-24
You can disable unity from the login without removing unity by moving the xsession file for Ubuntu.
Something like
```
sudo mv /usr/share/xsessions/ubuntu.desktop  /home/me/Documents
```
Change the home/me to your homefolder name.

And I would double check the xessions folder to see that the name is ubuntu.desktop.
You will also see entries for gnome-whatever in there.

But once the file is moved the entry for unity will not come up in the login.
And by simply moving it, if it does turn out to be problematic, you can move it back.

---

### Post by ben5 on 2014-10-24
perfect - thanks!

---

### Post by ben5 on 2014-11-05
> **deadflowr said:**
> You can disable unity from the login without removing unity by moving the xsession file for Ubuntu.
Something like
```
sudo mv /usr/share/xsessions/ubuntu.desktop  /home/me/Documents
```
Change the home/me to your homefolder name.

And I would double check the xessions folder to see that the name is ubuntu.desktop.
You will also see entries for gnome-whatever in there.

But once the file is moved the entry for unity will not come up in the login.
And by simply moving it, if it does turn out to be problematic, you can move it back.

Is it possible that there could be a problem logging in if this is done before gnome-fallback has ever been logged into?

I ask because I have people setting up PC's and they run a setup script as the admin user which moves the .desktop files out but when they go back to the limited user they are getting a message "Failed to start session"
The .desktop files are moved out before the limited user has ever logged int... could this cause a problem?  When I moved the .desktop files out on existing PC's where the limited user had already logged in there was no problem.  Any idea why?

---

### Post by ben5 on 2014-11-05
Curious... would it help if I not only move ubuntu.desktop out but rename gnome-fallback.desktop to ubuntu.desktop?

---

### Post by whitesmith on 2014-11-05
I would be careful to the verge of timidity in removing Unity. We simply have no idea how closely (or not) it is tied to the remainder of the code base. You certainly don't want to jump from the frying pan into the fire by causing aberrant behavior, especially with call center computers. What I would do is modify Grub so that Unity doesn't appear as a choice. This, at least, gives you and your users the safety of fallback in the event something goes awry.

---

### Post by ben5 on 2014-11-05
> **whitesmith said:**
> I would be careful to the verge of timidity in removing Unity. We simply have no idea how closely (or not) it is tied to the remainder of the code base. You certainly don't want to jump from the frying pan into the fire by causing aberrant behavior, especially with call center computers. What I would do is modify Grub so that Unity doesn't appear as a choice. This, at least, gives you and your users the safety of fallback in the event something goes awry.
Have you read over the thread or just my initial post?
Currently I am definitely not removing unity.  So far I have just moved [COLOR=#000000][FONT=Ubuntu Mono]/usr/share/xsessions/ubuntu.desktop out of the folder it is in to remove the option.  Though I think this might cause a problem if the user has never logged in before... See my previous post... What is this grub option you speak of?[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-11-05
Grub does not give the user an option as to which desktop session to load. That option comes at the LightDM login screen. And I think that you have already been given advice on how to remove the Ubuntu option.

If this issue is of such a concern to you, then you could always install Xubuntu or Lubuntu, especially if the machines are not coping too well with the requirements of Ubuntu. I expect that you also have provided your employees with a company policy statement as to the use of computers. It is for the employer to set policy and the employees to comply with policy. If it is your policy for your employees to use Gnome Session Flashback to give better customer service, then that should be enough for the employees.

I used to work for a major UK high street retailer and I had to sign various documents confirming that I had received this or that training and that I understood this or that company policy. Persistent failure to comply with company policy could lead to dismissal.

Just a few thoughts on the matter.

Regards.

---

### Post by deadflowr on 2014-11-05
> **ben5 said:**
> Is it possible that there could be a problem logging in if this is done before gnome-fallback has ever been logged into?

I ask because I have people setting up PC's and they run a setup script as the admin user which moves the .desktop files out but when they go back to the limited user they are getting a message "Failed to start session"
The .desktop files are moved out before the limited user has ever logged int... could this cause a problem?  When I moved the .desktop files out on existing PC's where the limited user had already logged in there was no problem.  Any idea why?

It might be that the sessions need to be toggled at login.
It is possible, though I can't remember, that the last session used will still be the set session at the login screen.
(Almost like a ghost)
A simple toggle, should cause that the disappear and only leave the gnome fallback sessions to choose from.

{Opinon
But overall, this is why I opted to use the move method, rather than the remove method. So if something odd does occur, you stiil have the original file on hand and moving it back into the xsessions folder will re-enable it if need be.

It is quite an ad-hoc method, but it does keep the system together without the need to fiddle around the system figuring out which pieces of unity(or pieces unity uses) you might need to run a functional fallback session.

I would think an even better method would be doing an install from [Ubuntu mini]("https://help.ubuntu.com/community/Installation/MinimalCD")
But that's a bit more complicated, though it would forego the unity environment altogether.}

---

### Post by whitesmith on 2014-11-06
> **ben5 said:**
> Have you read over the thread or just my initial post?
Currently I am definitely not removing unity.  So far I have just moved [COLOR=#000000][FONT=Ubuntu Mono]/usr/share/xsessions/ubuntu.desktop out of the folder it is in to remove the option.  Though I think this might cause a problem if the user has never logged in before... See my previous post... What is this grub option you speak of?[/FONT][/COLOR]

Yes, as a matter of fact I did read your post. May I be so bold as to suggest that it would behoove you to address with a modicum of civilly those who are attempting to be of assistance? We are all volunteers, not a paid help desk staff. You did not indicate your knowledge of Ubuntu so I assumed a passing degree of knowledge. Simply ignore my post and follow advice given by others. G'day!

---

### Post by ben5 on 2014-11-06
> **whitesmith said:**
> Yes, as a matter of fact I did read your post. May I be so bold as to suggest that it would behoove you to address with a modicum of civilly those who are attempting to be of assistance? We are all volunteers, not a paid help desk staff. You did not indicate your knowledge of Ubuntu so I assumed a passing degree of knowledge. Simply ignore my post and follow advice given by others. G'day!
Apologies I seem to have offended you.  I'm not sure which part of my post you found to be uncivil but I certainly had no intention of coming off that way.  :p

---

### Post by buzzingrobot on 2014-11-06
> **whitesmith said:**
> I would be careful to the verge of timidity in removing Unity. We simply have no idea how closely (or not) it is tied to the remainder of the code base.y.

There are a number of packages in the repos compiled against Unity libraries, so installing them on any distro that uses Ubuntu repositories will pull in, at least, those libraries as dependencies.

But, of course, that's not the OP's issue.

I wonder if the call center employees have any actual need for their own home folders?  Will they be creating/saving files specifically for their own use?  If not, that brings up the possibility that they don't need to log in when one shift replaces another. If the employer needs to record which employee did what, are the tools that do that tied to the username? (Even then, I wonder if a bit of a fake login could be scripted just to grab that name.)

---

### Post by ben5 on 2014-11-06
Thanks for all the input everyone!  :-)  FYI to explain our environment a little more.  The login is already generic.  "Interviewer" is the user name.  No need to tie anything to the person logging in.  After logging into ubuntu they SSH to a RHEL server and login to the survey software we use.  [I](i.e. dialer gives them calls and they read the screen and key in answers - everything important is on the server.  Ubuntu is just a thin client basically)

[/I]Currently I have decided that I would make the "setup" script that is run when the PC is first set up NOT move the unity.desktop out of the xsessions folder.  This way the guy who sets up the PC's can follow the old route of manually changing to gnome fallback and logging in.  Then in a daily script that is run each night, if unity.desktop exists I move it out.   So far I have had no problems when this is done AFTER the "Interviewer" user has manually logged into gnome-fallback.  They are able to login fine even after reboot.  

Regarding suggestions to use another distro.  Lubuntu, xubuntu, etc.   I played around with this some.  But found some of the things I wanted were a little easier to setup in Ubuntu and using gnome fallback gets me virtually the same performance as lubuntu/xubuntu did.   

Regarding employee policies... I would just enforce this with a policy for our normal office users... but the interviewers can't really be controlled or trusted.  There are hundreds of them.  If you don't want them to do something you have to make it impossible.  (Or at least hard.)  The supervisors are too busy to try to notice if people are not following rules and logging into Unity.  

Anyway - I *think *things will work OK with this change of waiting until Interviewer has been logged into manually before moving the unity.desktop file out of xsessions.  If not I will post back. 

Thanks again all!

---

