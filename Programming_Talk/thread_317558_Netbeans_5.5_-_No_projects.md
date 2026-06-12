---
title: "Netbeans 5.5 - No projects?"
date: 2006-12-12
forum: Programming Talk
---

### Post by HeavyAl on 2006-12-12
Hey all,

Just starting to program using the netbeans ide in Ubuntu. Used it a bit under Windows and was hoping for a similar setup.

Install went fine; installed JRE to my home dir, installed JDK to home dir (Both are  the new 1.6 vs) and then proceeded to install Netbeans 5.5. That went without a hitch as well.

Startup of the ide carries off without a hitch. No errors or warnings and the ide looks fine until I try to start one of the sample projects. 

Say I click General, then accept the defaults which creates the folder structure and files in my home dir, then I get a window for the readme.txt but there is nothing in the Project tree! The project tree doesn't even have the text at the top that is supposed to say 'project'. It's just empty.

Trying to open the project I dont find any project files to open either. Though if I just try to open a file I can see the build.xml, the manifest.mf and all the form files (which open and display the form data as expected) .. just no project navigation.

Anyone else had this problem?

I just checked the IDE log file and found this:

[org.netbeans.api.project.ProjectManager] Directory /home/me/AnagramGame was initially claimed to be a project folder but really was not

What the heck does that mean?

---

### Post by fritz_monroe on 2006-12-12
I've never used NetBeans, but to me, that looks like there's a config file wrong.  Take a look in the options and see if there's a way to change the default project directory.  In JDeveloper, you set this up for each project.

Good luck with this.

---

### Post by HeavyAl on 2006-12-12
Netbeans appears to create new directory for each project. It sticks them in my home folder. (/home/me/someproject).

Interesting. I used the update center in the IDE to install a bunch of addons which appeared to rerun some of the gui configuration scripts after which the project manager now works as expected!

Strange behavior but as long as I have a working IDE I guess I wont complain. 

Thanks for taking a look.

---

