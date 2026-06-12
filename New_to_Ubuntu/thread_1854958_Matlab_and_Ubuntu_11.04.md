---
title: "Matlab and Ubuntu 11.04"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by Phaddie on 2011-10-05
Hey guys,
  I just installed Ubuntu 11.04 last night on my pc.  This is my forst experience with a linux distro ever and I am assuming the issues I am having are because of my inexperience.

  Ubuntu installed ok.  I attempted to install matlab 2011a for linux and this is where I am having a problem.

 Matlab installed ok, activated ok, however when I try to run it all that happens is the Mtalab logo appears for about 5 seconds and then disappears and nothing else happens.  No Matlab and no errors.

 After a bit on internet searching it seems that Mathworks claims no support for Ubuntu 11.04 because of release date.  More searching seemed to indicate that some people are running it on 11.04.  There was a fix posted that was re linking some Java libraries, which i did.  The only change I saw was the logo now goes away in about half the time.

 If I drop to a terminal window and run it directly I get an error immediately that says:

matlab: no such file or directory (or something like that I am not at that computer now)

  I cannot even issue $ matlab -h for help say error happens.

  I assume there is an error log somewhere that will tell me what is happening?

  Any thoughts would be greatly appreciated. I am trying to avoid having to re install an older version of ubuntu (unless that is the only solution)

  -Phad

---

### Post by rmettier on 2011-10-05
Ok, let's try and figure out what's wrong.

The error message you're getting on the command line seems to indicate that the name of the actual binary you need to call isn't 'matlab', but something else. I can think of two things you can do:

1) right click on the launcher icon or menu entry that should start matlab (the one that only brings up the logo) and then choose 'properties'. Let us know what's in the 'command' field.

2) if that doesn't work, try typing 'apropos matlab' on the command line and see if that brings up anything.

---

### Post by Frogs Hair on 2011-10-05
Hello and Welcome 

There may be a solution at the link , but without knowing the exact error when you try to start from the terminal I don't know for sure .  [http://morganbye.net/blog/2011/05/matlab-ubuntu-1104](http://morganbye.net/blog/2011/05/matlab-ubuntu-1104)

---

### Post by deuxalucard on 2011-10-05
I installed yesterday but I make a launcher on the workspace to matlab, and its running, fine as always

---

### Post by Phaddie on 2011-10-05
> **rmettier said:**
> Ok, let's try and figure out what's wrong.

The error message you're getting on the command line seems to indicate that the name of the actual binary you need to call isn't 'matlab', but something else. I can think of two things you can do:

1) right click on the launcher icon or menu entry that should start matlab (the one that only brings up the logo) and then choose 'properties'. Let us know what's in the 'command' field.

2) if that doesn't work, try typing 'apropos matlab' on the command line and see if that brings up anything.


 As for step one, when I right click and go to properties there is nothing that shows command at all. And when I run apropos matlab in the terminal window it does nothing, just gives me back the prompt.

 As for the link posted that is the fix I already tried.

  When I run matlab in the terminal window this is the error I get:
matlab: command not found

  Thoughts?

---

### Post by Phaddie on 2011-10-05
Also, if I try to make a launcher in the workspace and just supply it with the matlab command, it will as well bring up the logo and then nothing (just tried it).

 @deuxalucard - do you just run the matlab script in the /bin directory or do you add anything after it?

   Phad

---

### Post by Kyledoo on 2011-10-05
I was having the same issue, what you need to do is navigate to the directory in which matlab is installed, then the bin directory within that, and then type ./matlab 
so for example, if it is in your home folder:
cd /home/<yourusernamegoeshere>/MATLAB/<your version of matlab(mine is R2011b)>/bin
then ./matlab
you may still get an error but it should run. The error is easily resolved by installing a package (more on that later if you need the help)
On a side note, I would like to have some sort of shortcut rather than having to navigate to it each time, does anyone know how to do this?

---

### Post by AskTell on 2011-10-05
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

try following these instructions.

---

### Post by Phaddie on 2011-10-05
> **Kyledoo said:**
> I was having the same issue, what you need to do is navigate to the directory in which matlab is installed, then the bin directory within that, and then type ./matlab 
so for example, if it is in your home folder:
cd /home/<yourusernamegoeshere>/MATLAB/<your version of matlab(mine is R2011b)>/bin
then ./matlab
you may still get an error but it should run. The error is easily resolved by installing a package (more on that later if you need the help)
On a side note, I would like to have some sort of shortcut rather than having to navigate to it each time, does anyone know how to do this?


 This worked!!! Now why did it work??

    Phad.

---

### Post by willyme on 2011-10-05
Configure the launcher (whatever one you are using) to launch Matlab with the "-desktop" argument.  So it should be:

(path to matlab directory)/bin/matlab -desktop

Now you don't have to have a terminal window open all the time.

---

### Post by Kyledoo on 2011-10-09
> **willyme said:**
> Configure the launcher (whatever one you are using) to launch Matlab with the "-desktop" argument.  So it should be:

(path to matlab directory)/bin/matlab -desktop

Now you don't have to have a terminal window open all the time.

Thank you! This makes things so much easier! I even downloaded the matlab logo to make it look legit :)

---

### Post by Robert Lock on 2012-03-29
After using the site [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) for the installation, you need to find the correct launch file.  For example, I'm running 64-bit R2011b, the launch file is NOT /usr/local/MATLAB/R2011b/bin/glnxa64/MATLAB, as you might expect, but rather, /usr/local/MATLAB/R2011b/bin/matlab.  I had the exact same problem with the splash screen appearing and then disappearing until I used the right launcher.

---

