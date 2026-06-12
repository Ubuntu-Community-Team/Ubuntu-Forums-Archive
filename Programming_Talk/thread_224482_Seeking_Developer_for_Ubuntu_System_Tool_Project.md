---
title: "Seeking Developer for Ubuntu System Tool Project"
date: 2006-07-28
forum: Programming Talk
---

### Post by SuperMike on 2006-07-28
I am seeking a mildly dedicated developer to take over and own a project I have started called Ubuntu System Tool (UST). It is designed to be like a "yast-lite", console-based tool for Ubuntu Server and Ubuntu Desktop.

I have already begun the project in Bash and VT100 codes and have a fairly functional menu system. Next steps are to build a template for data entry and to then turn it over to the community to write modules to enhance it, such as writing a module only for firewall editing, for instance.

The project has been approved for hosting at:

[http://sourceforge.net/projects/ust](http://sourceforge.net/projects/ust)

Please PM me through this website's PM feature or send me a PM via SourceForge to request more information.

[IMG]https://sourceforge.net/dbimage.php?id=82030[/IMG]

---

### Post by SuperMike on 2006-07-30
BTW, I guess I'm famous now. The project is now highlighted at fridge.ubuntu.com.

---

### Post by SuperMike on 2006-07-31
For some unknown reason it just got yanked off fridge.ubuntu.com. No answers yet as to why. But that's okay. We're pressing ahead.

---

### Post by LordHunter317 on 2006-07-31
I'm going to be frank with you.  I think you need to stop and go back to the drawing board.  I think you're setting yourself up for failure.

For starters, I'm not convinced you have a good idea.  SuSE is virtually the only distro left with a all-in-one configuration tool.  RedHat used to have one a long time ago.  It was called linuxconf.  They eventually abandoned it in favor of smaller tools that could do one task very well.

Now, I'm not saying RedHat is right.  But you haven't shown to anyone (including yourself) that your path is right, either.  You need to make a buisness case that a Yast-like ust tool is a good idea.  You need to state clear reasons why with both logical and technical support for them.  You also need to compare it to current state of system management on Ubuntu and show how it is better.  Finally, you need to show that it is better than other alternatives that could be done, like simply providing better documentation and education.

Second off, your implementation is flawed.  You won't be doing this in bash and VT100 codes, which are non-portable.  You don't want to start at the menus either.

You need to do so more design work before you start coding.  I'm not convinced you're ready to start coding.  If you need help with the design that's fine, ask for it.  But you're setting yourself up for failure if you start coding before you have a reasonable design.

---

### Post by ubuntu_demon on 2006-07-31
> **LordHunter317 said:**
> I'm going to be frank with you.  I think you need to stop and go back to the drawing board.  I think you're setting yourself up for failure.

For starters, I'm not convinced you have a good idea.  SuSE is virtually the only distro left with a all-in-one configuration tool.  RedHat used to have one a long time ago.  It was called linuxconf.  They eventually abandoned it in favor of smaller tools that could do one task very well.

Now, I'm not saying RedHat is right.  But you haven't shown to anyone (including yourself) that your path is right, either.  You need to make a buisness case that a Yast-like ust tool is a good idea.  You need to state clear reasons why with both logical and technical support for them.  You also need to compare it to current state of system management on Ubuntu and show how it is better.  Finally, you need to show that it is better than other alternatives that could be done, like simply providing better documentation and education.

Second off, your implementation is flawed.  You won't be doing this in bash and VT100 codes, which are non-portable.  You don't want to start at the menus either.

You need to do so more design work before you start coding.  I'm not convinced you're ready to start coding.  If you need help with the design that's fine, ask for it.  But you're setting yourself up for failure if you start coding before you have a reasonable design.
I like the idea of UTS. I'm assuming that the current implementation is just a mockup to attract attention and developers. 

I agree that there should be some focus on design first (after this mockup).

---

### Post by XVampireX on 2006-07-31
Why console? Isn't ubuntu supposed to be as newbie friendly as possible? Console shouldn't be used, and I'd rather have the all-in-one toolkit as a GUI program.

Good idea though, and don't get me wrong, I love the console for it's output, but still... make it a GUI.

---

### Post by ubuntu_demon on 2006-08-01
> **XVampireX said:**
> Why console? Isn't ubuntu supposed to be as newbie friendly as possible? Console shouldn't be used, and I'd rather have the all-in-one toolkit as a GUI program.

Good idea though, and don't get me wrong, I love the console for it's output, but still... make it a GUI.
Having a console based tool which gives easy acces to a lot of important commands would be nice for servers.

If you want a GUI control center you should look here :

Ubuntu Control Center
[http://www.ubuntuforums.org/forumdisplay.php?f=157](http://www.ubuntuforums.org/forumdisplay.php?f=157)

---

### Post by ubuntu_demon on 2006-08-01
> **SuperMike said:**
> For some unknown reason it just got yanked off fridge.ubuntu.com. No answers yet as to why. But that's okay. We're pressing ahead.
Do you know why already ?

When the UST article was still on the fridge I started a thread about the UST here :
[http://ubuntuforums.org/showthread.php?t=226311](http://ubuntuforums.org/showthread.php?t=226311)
and I added it to my blog here :
[http://ubuntudemon.wordpress.com/2006/07/31/planning-the-ubuntu-system-tool-ust](http://ubuntudemon.wordpress.com/2006/07/31/planning-the-ubuntu-system-tool-ust)

---

### Post by sas on 2006-08-01
I think I heard on IRC that one of the reasons it got pulled was because other websites were picking it up and advertising it as an official ubuntu project as the original fridge post wasn't too clear.

---

### Post by SuperMike on 2006-08-01
> **XVampireX said:**
> Why console? Isn't ubuntu supposed to be as newbie friendly as possible? Console shouldn't be used, and I'd rather have the all-in-one toolkit as a GUI program.

Good idea though, and don't get me wrong, I love the console for it's output, but still... make it a GUI.

Sorry, won't go there. This project is primarily for Ubuntu Server, which will be without a GUI in most reasonable installations that I can think of, but Ubuntu Desktop will also work with it. In fact, it might be made to work with 80% functionality on Debian, in fact.

This TUI is designed to help out those who have a console-based server as its primary goal.

---

### Post by SuperMike on 2006-08-01
> **sas said:**
> I think I heard on IRC that one of the reasons it got pulled was because other websites were picking it up and advertising it as an official ubuntu project as the original fridge post wasn't too clear.

Interesting. Nope, not an official Ubuntu project and no I didn't mean to offend anyone at all at Canonical. If the Ubuntu dev team or the Canonical employees want me to take "Ubuntu" out, I'll be happy to do it. I just would like to ask that someone give me suggestions, instead.

The main thing that readers of this should keep in mind, however, is that this tool will be designed for Ubuntu. That's why I called it "Ubuntu System Tool" instead of "Fedora System Tool" or "Debian System Tool". It's just not my focus to make it a ubiquitous tool for all platforms, or even for all Debian-based platforms.

---

