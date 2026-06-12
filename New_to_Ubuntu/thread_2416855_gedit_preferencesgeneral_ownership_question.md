---
title: "gedit preferences/general ownership question"
date: 2019-04-16
forum: New to Ubuntu
---

### Post by hellander on 2019-04-16
Greetings Ubuntu Community, this is my first post! ^^
I got a few questions so I'll go through the problem and add the questions in order.

Went to write a small C program in Linux, found a quick guide showing these steps: **gedit file.c** -> **gcc file.c -o programName** -> **./programName **, and that worked nicely.  

 -_1. question_: I found it a bit cumbersome going through gedit, gcc and  ./ each time I wanted to change a small bit of code. I'm sure it'd get much cleaner and faster with experience, but up until now I was  coding on Windows in Codeblocks/Eclipse, should I just use an IDE like that on Linux as well?

While writing the program I changed a few settings like *auto indent, numbered lines, highlight line*, etc. (Note, the actual *Preferences* option in the menu tab was not there, I used the two tabs in the bottom right corner) However, I noticed that each time I went to edit the program again, the settings I changed were not being saved - they were being reverted back to default.

I tried running** sudo gedit** and changing the settings that way (this time the *Preferences* option was there) and this time my settings would be there if I ran **sudo gedit**, but not when running without **sudo**.

After doing some Googling, I found some suggestions to change the ownership of a gedit config file (didn't work, file not found) and that I shouldn't be using sudo for gui apps, but **gksudo**/**gksu**/**pkexec**.
 
 -_2. question_: So, running gedit as superuser would let save the  settings, but running as a 'regular' user wouldn't. Is there a way to  let the regular user change the settings of the gedit gui? I've only got  one user account on this PC anyway.

Trying to run **gksudo gedit** and **gksu gedit** gave me the error: "Command gksu/gksudo not found.". Trying to run **pkexec gedit** gave me the error:

> Unable to init server: Could not connect: Connection refused

(gedit:23394): Gtk-WARNING **: 19:34:18.600: cannot open display: 

From what I gather, **gksudo/gksu** is no more, **pkexec** should work, but I may need something called a *policy*?

---

### Post by DuckHook on 2019-04-16
Please read [this]("https://ubuntuforums.org/showthread.php?t=1486138"), especially the part dealing with policykit and *nautilus-admin*

---

### Post by deadflowr on 2019-04-16
You shouldn't have to run as root to change or set gedit's preferences.
(In fact most changes done this way don't even translate to your user's own preferences anyway)
You should be able to make the change through dconf/gsettings.
And those changes should stick.

That can be doable through dconf editor which you can install.
You can find it in the Software program,
or run
```
sudo apt install dconf-editor
```
gedit preferences are in org > gnome > gedit > preferences. (for most of what you want those are in the editor section)

---

### Post by TheFu on 2019-04-16
Unix doesn't need an IDE. The entire OS is the IDE.

No need to close whatever editor you use down between compile, debug or running the program.  
Open 3 terminals.
1) Editor - which ever one you like.  gedit is like "notepad", nobody would use it for programming.
2) Make - this is where you build software
3) Run - this is where you run the program.
If you setup the mouse policy to be focus-follows-mouse, then you can just slide the pointer over the window you want active, don't click. Don't have it pulled to the top.  Just slide the mouse over, use the !! or up arrow to run the compile/link steps. Move to the "run" window and use the !! or up-arrow to rerun the program.

When you program becomes non-trival, you'll want to use Makefiles or CMake to control building the software in an efficient way.
Also, you'll want an integrated editor/debugger. Geany does that for C/C++.

Understanding how to control these things manually, means you won't be stuck using some IDE which sucks RAM, CPU, GPU over nothing.  Where I've worked, we had low-end workstations that were used to log into beefy compile servers. No way to use an IDE in that environment.

For software development, there should **never** be any need to use sudo for the editor or builds and only use sudo for running daemon programs, not end-user programs. If you aren't working on a system daemon, then NEVER use sudo for anything related to your program.  I suspect you did something bad early on and don't recall doing it.  Run this:
```
sudo chown -R $LOGNAME $HOME
```
You can check the manpage for chown to understand what that does.  It will have your userid take ownership of all files in your HOME directory, recursively.  In no world would that not be 100% safe.  Unix system files under the userid HOME should be owned by the userid. I suspect you ran sudo gedit during your first login and that toasted the file and directory permissions. The command above will fit it and your userid will have access to the settings again.

Don't use sudo/gksudo/pkexec with GUI programs.  Just don't.

If you need to edit system config files, use **sudoedit /path/to/file**  Whatever editor is set in the EDITOR environment variable will be used. You can use gedit in that variable, if you like. It is safe.


BTW, there are 50 other editors on Linux, almost all of them better than gedit.  People like atom, geany, vim, emacs. So it is probably worth your time to check out at least those.  Once you see vim in the hands of an expert, you'll never look at the other editors except as toys.

Google a few things to get more descriptions:
"Unix as an ide" - [https://sanctum.geek.nz/arabesque/series/unix-as-ide/](https://sanctum.geek.nz/arabesque/series/unix-as-ide/)
"pick unix editor" - [https://fossbytes.com/9-best-text-editors-linux-programming-2017/](https://fossbytes.com/9-best-text-editors-linux-programming-2017/)
And the reason why your gedit configs cannot be saved, [https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications](https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications) - the first 2 answers are most likely correct for your situation. 

 It is easier to say "never" since that would apply to users who don't know better and cannot be bothered to learn and understand Unix file and directory permissions.  As a programmer, you don't have that luxury.  Spend the 45 minutes working through all the possible file permissions using 3 different userids and at least 2 different groups.  Along the way, something should "click" and you'll have mastered permissions for every Unix-like operating system in the world, which is basically all of them, except 1.

---

### Post by hellander on 2019-04-16
Thanks for all the help, you guys rock! :)

> **DuckHook said:**
> Please read [this]("https://ubuntuforums.org/showthread.php?t=1486138"), especially the part dealing with policykit and *nautilus-admin*

I'll definitely be more cautious with my use of sudo after that read and Fu's advice.
I've installed the nautilus-admin package just for good measure (found out it was already installed anyway) and I've decided not to delve into the policy business just yet considering what you guys told me, I think it's unnecessary to try and find workarounds for getting gui's into sudo, for now.

> **deadflowr said:**
> You shouldn't have to run as root to change or set gedit's preferences.
(In fact most changes done this way don't even translate to your user's own preferences anyway)
You should be able to make the change through dconf/gsettings.
And those changes should stick.

That can be doable through dconf editor which you can install.
You can find it in the Software program,
or run
```
sudo apt install dconf-editor
```
gedit preferences are in org > gnome > gedit > preferences. (for most of what you want those are in the editor section)

Your suggestion has indeed worked! I was able to make the changes and they have indeed remained the same even after closing.

> **TheFu said:**
> Unix doesn't need an IDE. The entire OS is the IDE.

No need to close whatever editor you use down between compile, debug or running the program.  
Open 3 terminals.
1) Editor - which ever one you like.  gedit is like "notepad", nobody would use it for programming.
2) Make - this is where you build software
3) Run - this is where you run the program.
If you setup the mouse policy to be focus-follows-mouse, then you can just slide the pointer over the window you want active, don't click. Don't have it pulled to the top.  Just slide the mouse over, use the !! or up arrow to run the compile/link steps. Move to the "run" window and use the !! or up-arrow to rerun the program.

When you program becomes non-trival, you'll want to use Makefiles or CMake to control building the software in an efficient way.
Also, you'll want an integrated editor/debugger. Geany does that for C/C++.

Understanding how to control these things manually, means you won't be stuck using some IDE which sucks RAM, CPU, GPU over nothing.  Where I've worked, we had low-end workstations that were used to log into beefy compile servers. No way to use an IDE in that environment.

For software development, there should **never** be any need to use sudo for the editor or builds and only use sudo for running daemon programs, not end-user programs. If you aren't working on a system daemon, then NEVER use sudo for anything related to your program.  I suspect you did something bad early on and don't recall doing it.  Run this:
```
sudo chown -R $LOGNAME $HOME
```
You can check the manpage for chown to understand what that does.  It will have your userid take ownership of all files in your HOME directory, recursively.  In no world would that not be 100% safe.  Unix system files under the userid HOME should be owned by the userid. I suspect you ran sudo gedit during your first login and that toasted the file and directory permissions. The command above will fit it and your userid will have access to the settings again.

Don't use sudo/gksudo/pkexec with GUI programs.  Just don't.

If you need to edit system config files, use **sudoedit /path/to/file**  Whatever editor is set in the EDITOR environment variable will be used. You can use gedit in that variable, if you like. It is safe.


BTW, there are 50 other editors on Linux, almost all of them better than gedit.  People like atom, geany, vim, emacs. So it is probably worth your time to check out at least those.  Once you see vim in the hands of an expert, you'll never look at the other editors except as toys.

Google a few things to get more descriptions:
"Unix as an ide" - [https://sanctum.geek.nz/arabesque/series/unix-as-ide/](https://sanctum.geek.nz/arabesque/series/unix-as-ide/)
"pick unix editor" - [https://fossbytes.com/9-best-text-editors-linux-programming-2017/](https://fossbytes.com/9-best-text-editors-linux-programming-2017/)
And the reason why your gedit configs cannot be saved, [https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications](https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications) - the first 2 answers are most likely correct for your situation. 

 It is easier to say "never" since that would apply to users who don't know better and cannot be bothered to learn and understand Unix file and directory permissions.  As a programmer, you don't have that luxury.  Spend the 45 minutes working through all the possible file permissions using 3 different userids and at least 2 different groups.  Along the way, something should "click" and you'll have mastered permissions for every Unix-like operating system in the world, which is basically all of them, except 1.

I will definitely try the 3 terminal setup! I haven't used the focus-follows-mouse policy, but it seems very efficient.

Since I just wanted to quickly test something in C, I didn't really bother searching for the best Linux text editors and since I saw gedit had a lot of the basic settings to make it more into a programming text editor I thought it might do the job. I also like the idea of the default editor doing the job so I wouldn't need to install more apps that do very similar things - I dislike cluttering (Although, the way Linux works it seems I could always delete gedit and get a different editor if I wanted to?). I'll still take your advice and see what the other editors have to offer though.

I do have another question: since you said I'd want Geany I read-up on on it and saw it's an IDE? If I used Geany I should be able to code/compile/debug in it and wouldn't need to use 3 terminals/text editors at all?

---

### Post by oldrocker99 on 2019-04-16
My go-to editor is nano, already installed.
```
sudo nano textfile
```

Learned about it about 2007, and I've used it ever since.

Programmers love geany, or so I have heard.

---

### Post by TheFu on 2019-04-16
I purge nano on every new system.  It is the default for a few things that I quickly modify on any new box. Drives me crazy.  Once nano is gone, vim becomes the default. For me, purging nano solves multiple problems immediately, 1 command, 10 solutions.  ;)   I don't care if someone else needs a really simple editor on my systems. Most are servers, so no GUI anyways. The desktops are so customized (minimal GUI, no menus) which would make most people think the system was broken.  These aren't general access systems.
 
> I do have another question: since you said I'd want Geany I read-up on on it and saw it's an IDE? If I used Geany I should be able to code/compile/debug in it and wouldn't need to use 3 terminals/text editors at all? 

Geany isn't a full IDE. It is a minimal, lite, IDE.  You'll have to manually setup everything if you want the debugger and compiler to work.  Also, the real power of developing on Unix is automation.  80% of the power in Unix comes from this. If you want to limit yourself to only 20% of the power, stick with GUI tools.  When your development matures to using CI and TDD, you'll be stuck with Geany of you use it more than as an editor with a lite-debugger capability.

Editors are lite. It isn't like you are installing Eclipse which is like installing MS-Outlook and iTunes on a Pentium-1 PC with 128MB of RAM. Slow.  More programs are just disk space and on Unix, they are tiny.  My development desktop has ...
```
$ df .
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        20G   16G  2.2G  89% /

``` 20G of storage. That includes the OS and my programming tools and git repos.  That's over a decade of perl code. Every year or so, I'll remove an old version of perl, but I usually keep 3+ full perl development environments and switch between them as needed.  
I'm a heavy user of virtual machines for deployments. I should use Containers more to lower the overhead. Maybe this May will be when I do that.

Don't forget to learn git along the way too. Even if you work alone, good use of code version control will save you from yourself.  Anyway, please, please, please, make automatic, daily, versioned, backups of anything you can't afford to lose.

I'll be happily programming in vim, where I'm most efficient.  But everyone needs to find their own way to vim. Eventually, you'll come around. Everyone does.  In the beginning, just learn 1 new chord in vim each week, beyond the normal 30 that everyone uses daily. I wasted 6 months using emacs.  Eventually, I was switching emacs into vi-mode all the time to get anything done.  After a month of that, I decided to skip the extra bloat (emacs) and just use vi.  That was 1994.

The only editor I've ever seen on any router is vi/vim.  A basic understanding of it is REQUIRED.  At least spend the time with vim to get the minimal skills. Not knowing a minimal level of vim is like not knowing how to add gas to a car.

---

### Post by Impavidus on 2019-04-17
> **hellander said:**
> 
While writing the program I changed a few settings like *auto indent, numbered lines, highlight line*, etc. (Note, the actual *Preferences* option in the menu tab was not there, I used the two tabs in the bottom right corner) However, I noticed that each time I went to edit the program again, the settings I changed were not being saved - they were being reverted back to default.

I tried running** sudo gedit** and changing the settings that way (this time the *Preferences* option was there) and this time my settings would be there if I ran **sudo gedit**, but not when running without **sudo**.

After doing some Googling, I found some suggestions to change the ownership of a gedit config file (didn't work, file not found) and that I shouldn't be using sudo for gui apps, but **gksudo**/**gksu**/**pkexec**.
 
 -_2. question_: So, running gedit as superuser would let save the  settings, but running as a 'regular' user wouldn't. Is there a way to  let the regular user change the settings of the gedit gui? I've only got  one user account on this PC anyway.
When you run gedit with sudo to change the settings, you'll change gedit's settings for the normal user, but the config file containing the settings will be owned by root. This makes it impossible for the normal user to save settings changes later. So make sure the config file is owned by your ordinary user. All files in your home directory should be owned by your ordinary user. TheFu gave you the chown command.

> **TheFu said:**
> Unix doesn't need an IDE. The entire OS is the IDE.

No need to close whatever editor you use down between compile, debug or running the program.  
Open 3 terminals.
1) Editor - which ever one you like.  gedit is like "notepad", nobody would use it for programming.
2) Make - this is where you build software
3) Run - this is where you run the program.
If you setup the mouse policy to be focus-follows-mouse, then you can just slide the pointer over the window you want active, don't click. Don't have it pulled to the top.  Just slide the mouse over, use the !! or up arrow to run the compile/link steps. Move to the "run" window and use the !! or up-arrow to rerun the program.You can also use multiple workspaces. Put each window in its own workspace at maximum size, use ctrl+alt+arrow to switch from one to the other. No need to use a mouse.

I also use vim as my editor. I've 15 workspaces, most of them with at most one application window at a time: one for a web browser to find documentation, one for the editor for source code, one for the compiler, one for running, one or two for reading man pages, one or two to view/edit the input/output files of my program etc.

With 15 workspaces in a 3×5 layout, each in 16:9 aspect ratio, the combined grid has 16:15 aspect ratio, which is as close to square as I could reasonably get it.

---

### Post by oldrocker99 on 2019-04-17
> **TheFu said:**
> I purge nano on every new system.  It is the default for a few things that I quickly modify on any new box. Drives me crazy.  Once nano is gone, vim becomes the default. For me, purging nano solves multiple problems immediately, 1 command, 10 solutions.  ;)   I don't care if someone else needs a really simple editor on my systems. They are so customized (minimal GUI, no menus) which would make most people think the system was broken.


Well, there you go. We do have a lot of choices for a text editor, and we all have favorites. I do seldom use nano except for editing a few files in /etc.

---

### Post by him610 on 2019-04-19
@TheFu
> I purge nano on every new system. It is the default for a few things that I quickly modify on any new box. Drives me crazy. Once nano is gone, vim becomes the default. For me, purging nano solves multiple problems immediately, 1 command, 10 solutions.
Why? What is about *nano* that so upsets you? The world wants to know.

---

