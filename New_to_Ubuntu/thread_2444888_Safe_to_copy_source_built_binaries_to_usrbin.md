---
title: "Safe to copy source built binaries to /usr/bin?"
date: 2020-06-05
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-06-05
Hello all,

Is it safe to copy binaries built from source to /usr/bin so they can be called without needing the full file-path?

I know it sounds like a dumb question but I know sometimes seemingly harmless stuff can be less than ideal for 'special Linux reasons' that nobody would ever just think of off of the top of their head.

Thanks

---

### Post by ajgreeny on 2020-06-05
Simpler, and maybe safer, depending on what they are, to copy them to ~/bin in your home which is automatically added to $PATH if it exists.

---

### Post by SeijiSensei on 2020-06-05
I follow the standard of most source code which is to put everything under /usr/local.  /usr/local/sbin and /usr/local/bin are in the default path set by Ubuntu, and ldconfig is already set up to look in /usr/local/lib.  Oftentimes configuration files will then end up in /usr/local/etc.

Usually "sudo make install" will use /usr/local unless you chose something else during the ./configure stage.

If you're talking about binaries for which you don't have source and did not run the usual "./configure; make; make install" then whether you can copy those binaries directly is more iffy.  Unless the binary is "statically-compiled" it will depend on files in places like /lib and /usr/lib that you may not have.  I would rely on the repositories for any file that ships with Ubuntu, for instance, using the repository version of Firefox rather than the binary on its site.  I only compile software when it doesn't exist in a repository, or the repository version lacks features I desire.

---

### Post by ActionParsnip on 2020-06-06
Or /opt
The package system will blindly overwrite files it finds with new ones during updating. You could make a deb if your efforts which will make packages not be able to overwrite files as it will be seen as part of a different package (an overlap) and stop. 
Using /opt and adding the directory to $PATH avoids all of this and makes things easier

---

### Post by TheFu on 2020-06-06
Good question.  If you aren't around Unix people all the time, lots of these questions exist that take nothing to know, but there are subtle reasons for specific answers.  A 2 minute chat can clear up this stuff easily. There are thousands of similar types of questions.

For commonly used tools, typically F/LOSS, I'd go with /usr/local/ method if they need to be available for everyone on the system. Just be certain you add /usr/local/ to your backups.

For tools that are only for me, I put them into ~/bin/ which I have added to the PATH in my ~/.bashrc.

For commercial tools or complex packages made up of many different, tightly coupled programs that are provided as binary installs, not with source, I place those into /opt/.  Think of something like Zimbra and a complex apache+tomcat+jetty+mariaDB service.  In theory, zimbra parts can be replaced, but in practice, the 15 different F/LOSS programs involved are tightly coupled.

For most things on a Unix system, there are long-standing reasons for why things are the way they are. Some really brilliant people worked on these solutions decades before us. When something doesn't make sense, there is probably a good reason that we just don't know yet.

If you haven't been told about this book [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is is worth skimming. Stop where something grabs your interest and go deeper.  It is a "what" book, not a "why" book.  Most books aren't good at the "why" - that's where a mentor or LUG can help.

---

### Post by jcdenton1995 on 2020-06-06
Hi there,

There isn't a ~/bin on my system by default, I tried adding it but binaries stored in there can't be called using only their name. I'm sure I could fix that but I'm keen to try and keep things consolidated instead of spreading files around if I cam help it.

Is it really bad practice to use /usr/bin? My other binaries I installed from the package manager are stored there.

---

### Post by monkeybrain20122 on 2020-06-06
No, just create a new folder called bin in your $HOME  (or ~/.local/bin though I prefer it not be hidden) and put your bin file there. Logout and login (since the folder didn't exist before) then it will be in your $PATH.

You don't want to corrupt your file system, the other binaries installed by package manager store there but the package manager keeps track of them, it won't keep track of stuffs you put there.

---

### Post by jcdenton1995 on 2020-06-06
Hello!

I don't actually have a /usr/local/bin, only /usr/local/sbin.

I only have one other binary that I built from source, a tool called 'jstest-sdl' which automatically installed itself in /usr/bin so I got the impression that was the default location for user installed stuff?

On your last point yes I haven't been compiling anything that can be had from the repo unless totally necessary, the binary in question is just a tool called 'heimdall-flash' that's basically an open source copy of Samsungs Odin tool for flashing things to Samsung phones. For some reason the repo version is known to not work with some phones (it is an older version so maybe that?) but if one compiles the latest version it works okay. I'd prefer not to self install though as I believe it can sometimes be tricky to remove stuff that has been plonked wherever the makefile decides?

---

### Post by monkeybrain20122 on 2020-06-06
That's why if you compile from source it is better to use checkinstall (sudo apt install checkinstall) instead of doing make install because that way it creates a .deb then install it so that the package manager can keep track.

---

### Post by jcdenton1995 on 2020-06-06
Ah I need to log out/in! That's the missing piece...

Will it really corrupt anything though? I understand that the package manager keeps track of all the things installed via itself but will a few intruders cause a problem? (not a rhetorical question I honesty have no idea)

Edit: also regarding your comment about check install, that sounds very interesting and I'll deffo look into that

---

### Post by jcdenton1995 on 2020-06-06
@TheFu Thanks for the detailed reply, I'll take a look into the book as I much prefer quickly thumbing through a book I can grab to having to search the interwebz every time I need a command.

As for unix like systems, I think it's cool how they seem to have this really rich history which I have sometimes found helpful in understanding some conventions, like the X server - to a layman like me it seems confusing and ridiculous until you remember that unix was like a distributed system, so its like having the conventions of a distributed system, but its just all on my laptop.

---

### Post by TheFu on 2020-06-06
> **jcdenton1995 said:**
> Hi there,

There isn't a ~/bin on my system by default, I tried adding it but binaries stored in there can't be called using only their name. I'm sure I could fix that but I'm keen to try and keep things consolidated instead of spreading files around if I cam help it.

Is it really bad practice to use /usr/bin? My other binaries I installed from the package manager are stored there.

/usr/bin is for APT packaged managed programs on Debian/Ubuntu and APT-based systems.  if you install a special version of some binary there then somehow the package manager decides to install a version too, then your version will be overwritten AND the package manager will think that file is under its management.

You should get used to making directories that are common and needed when they are needed.  ~/bin is one of those.  Same for /usr/local/bin/.

Don't confuse "users" with "admins".  Users can only write to their HOME and /tmp/.  Admins can write almost everywhere.  Never forget, all Unix-like systems are multiuser even if you are the only human using the system.  The OS knows there is a difference. Well, not really, but file permissions handle those differences.  Don't screw up file permissions for programs.  

As for logging out and logging back in to see changes,  that isn't strictly needed except to have the gui know things.  Any terminal can be brought up and should see any new programs in a modified PATH.  Every running shell will automatically see new files w/ execute permissions that is created in any directory already in the PATH.

Managing a PATH is a day-3 skill in my beginner Linux classes. it isn't hard and MS-Windows uses the PATH EXACTLY the same way.

> conventions of a distributed system, but its just all on my laptop.
Your laptop is still a Unix system whether you use it that way or not.  Using network storage, running programs on other systems to be displayed locally, remotely logging into other systems are all built into Linux and have been since 1991.

---

### Post by jcdenton1995 on 2020-06-06
> **TheFu said:**
> /usr/bin is for APT packaged managed programs on Debian/Ubuntu and APT-based systems.  if you install a special version of some binary there then somehow the package manager decides to install a version too, then your version will be overwritten AND the package manager will think that file is under its management.

You should get used to making directories that are common and needed when they are needed.  ~/bin is one of those.  Same for /usr/local/bin/.

Nice one thanks, that makes sense. I went ahead and made ~/bin and have moved a couple of source built binaries into it, one of them was actually put in /usr/bin/ by 'make' so I guess that goes to show that you cant always trust where files get dropped...

---

### Post by monkeybrain20122 on 2020-06-06
> **TheFu said:**
> 
As for logging out and logging back in to see changes,  that isn't strictly needed except to have the gui know things..

He needs to login and logout because ~/bin didn't exist last time he logged in, and .bashrc only gets run when logout and login again (though you can run source ~/.bashrc without logging out)

---

### Post by monkeybrain20122 on 2020-06-06
Actually for my own set up I compile the software in ~/opt (I created the directory), then either symlink the binary to ~/bin or put a script in ~/bin to run the actual binary if some nonstandard environmental variables need to be set first. If install for system, then it gets installed to /usr/local

---

### Post by TheFu on 2020-06-06
Most source build tools/makefiles have a way to set the "PREFiX" to /usr/local/ to prevent that issue.  Projects that build packages for RPM and APT would probably default to /usr as the prefix, but Debian and Canonical don't just grab the latest versions of software for a release. 

That's why we often have 2 yr old versions of some packages even in fresh releases.  if you need a newer version, use a trusted PPA for the software.  Source code is probably the least best of the choices for installing compiled software. 

Using source means that you accept the responsibility to patch, build and install the newer versions on your system(s).  That defeats the reasons to use a curated Ubuntu OS install.  Sure, there are times when there isn't any choice and it has to be done.  Those times should be limited and avoided when possible.  Packages for scripted tools are a little less bad and less hassle to maintain, usually.  Just depends on any dependencies for the package/software.

My ~/bin/ is full of custom scripts that aren't systems related.  All scripts start there and as they become "Production quality" and if they are safe for other users, then they would be moved to /usr/local/bin/.   Scripts that are specific for admin tasks go into /usr/local/sbin/

What directories should be used to hold is spelled out in the FHS.   Most Unix systems follow this. There's a wikipedia page about those standards.  Except that the Canonical Snap team doesn't seem to have ever read the FHS, unfortunately.

---

