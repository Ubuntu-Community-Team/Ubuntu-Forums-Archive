---
title: "ntfs open source driver for external hard drive"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by anthonyglamis on 2008-08-13
Hi,
  I have posted recently about not having a internet connection.   So I am basically trying to download packages and install them manually, by the way I have feisty fawn. I was previously trying to install VLC and have since put that on the back burner.  I am trying to install an open source ntfs driver since I have a maxtor 1 gig drive that i would like to transfer movies to.  Well Ubuntu see's this drive just fine but I do not have any write priveledges....go figure.  I thought by downloading this package and using the install instructions I would be good to go.  Can someone please let me know where I have gone wrong.  Here is what happend.

  I downloaded the NTFS-3G open source driver for my external HD from here.  [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

  I extracted the files to a directory /media/sda1/temp

  While logged in as root and in that current directory I typed..
./configure  
this command was good as some other files were created in that directory.  I then typed...
  make  
nothing happend with this it says make: *** no taregts specified and no make file found.  stop.  I also tried...
  make install
this says no rule to make target "install"  stop.  

A little help would be fantastic.  Thanks all.

---

### Post by ibutho on 2008-08-13
The problems you describe can happen if the ./configure script did not finish successfully. After running ./configure, check to see if there are no error messages printed on the screen.

---

### Post by anthonyglamis on 2008-08-13
I will check to see if there are any errors.  If there are not what would that tell me?  Also would I need to be typing 
sudo make install 
or was the command correct to begin with?

---

### Post by ibutho on 2008-08-14
If "make" did not run successfully, then there is no point in doing "make install" because the program did not build successfully. The "makefile not found" error is what makes me suspect that "./configure" did not finish correctly. If it had, then you would have the makefile.

---

### Post by anthonyglamis on 2008-08-14
I'm sorry but I tried to save the file and apparently did not save the file correctly.  Basically you were right I wasn't even paying attention, there was an error during the process of ./configure

it said something like command ./configure cannot compile an executable

I'm sorry I know that is probably not exactly the output but it is pretty close.  Does anyone know what the issue might be?  Did I get a bad download or am I missing some type of tool that allow me to run the ./configure command?

---

### Post by anthonyglamis on 2008-08-14
bump for a reply.....

---

### Post by nothingspecial on 2008-08-14
May I make a couple of possibly unusefull suggestions.
Download and install either Gutsy or Hardy where ntfs read and write is installed by default.
Or reformat your ext hardrive to a linux compatible file system.

---

### Post by anthonyglamis on 2008-08-14
that sir may not be a bad idea but i would like to fix this rather than reload a operating system.  I just read that i might have to have build essential loaded for the command ./configure to compile whatever it needs to compile.  Would this be true?  Also would I be able to install build essential without having a program like build essential already on my computer?  Weird question huh?

---

### Post by nothingspecial on 2008-08-14
yes you do need build essential

---

### Post by cariboo on 2008-08-14
If you look here:

[http://packages.ubuntu.com/hardy/ntfs-3g](http://packages.ubuntu.com/hardy/ntfs-3g)

I know this is for hardy, but you will probably need these files also to get ntfs-5g to work properly. As one of the previous posters stated, it might be an idea to update to a newer version of Ubuntu, as Fiesty is no longer supported. You can have a cd shipped to you if you go here:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Request a free CD.

Jim

---

### Post by anthonyglamis on 2008-08-14
interesting....how does one get build essential without an internet connection?  lets see if google is my friend.  My next question is will i even be able to install build essential or is it something that must be installed during ubuntu installation?

---

### Post by nothingspecial on 2008-08-14
Anthony, I`m not being funny here but you obviously have an internet connection somewhere in Iraq.
Could you not just borrow it for 1/2 an hour, get all the packages you require and thank the provider accordingly.
Linux was built over the the internet and the world wide web is pretty essential to configure it. Yes it is possible without one but damn hard.

---

