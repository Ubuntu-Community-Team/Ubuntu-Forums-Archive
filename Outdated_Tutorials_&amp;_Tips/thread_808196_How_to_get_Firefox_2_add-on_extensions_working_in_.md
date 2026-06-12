---
title: "How to get Firefox 2 add-on extensions working in Firefox 3"
date: 2008-05-26
forum: Outdated Tutorials &amp; Tips
---

### Post by lotuseclat79 on 2008-05-26
Here is how I got the Update Notifier 0.1.5.3 add-on extension which states it is not compatible with Firefox 3 to work in Firefox 3.0b5 in Ubuntu 8.04 LTS Hardy Heron.

1) open up a new tab, enter about:config in the address bar. Create a new item named extensions.checkCompatibility, boolean, and set it to false.

2) visit the add-on web page you want to install (I suggest the one I am using in this example) to get you started with the methodology.

Note: the methodology is that we are going to intercept the FF add-on as it is staged to be installed, but before it is installed, so at the point in time after you are able to download the add-on, [highlight]DO NOT RESTART Firefox in the instructions below until I tell you to do so[/highlight].

If your Firefox browser tells you that the add-on is for an older version of Firefox, click on the link that shows all of the older versions.

On that web page, you may be able to click on the latest version (probably for FF 2.0.0.*), and go through the normal scenario of downloading the add-on (if you get a green button to click). If you can successfully do this, then [highlight]DO NOT RESTART Firefox after the download[/highlight]. If you cannot successfully download the add-on, you can also try to visit the add-on author's web page and try to download it from there - again - if you can successfully download it - [highlight]DO NOT RESTART Firefox after the download[/highlight].

Next is the method for updating the add-on to work in FF 3 which is to perform a very simple edit in the install.rdf file for the extension.

In order to intercept the add-on zipped tmp.xpi file, (in Linux only for this method), do the following commands from a Terminal window:
```

# go to your home directory in Ubuntu - i.e. /home/ubuntu
$ cd
$ cd .mozilla/firefox/*.default/extensions/staged-xpis/*
$ cp tmp.xpi ~/Desktop
$ cd ~/Desktop
$ mkdir stage
$ mv tmp.xpi stage
$ cd stage
$ unzip tmp.xpi
$ mv tmp.xpi ~/Desktop

```

At this point, simply edit the install.rdf file for maxVersion from 2.0.0.* to 3.0+ and save the edit in the install.rdf file. Now we are ready to zip up the file again and replant it into the staged-xpis/* subdirectory as a revised tmp.xpi file.  

Note: Beginners should probably make the edit with the command, while intermediate and expert users can use the vi command.  Note: Don't forget to Save the edit!:
```

$ gedit install.rdf

```

In the stage directory, i.e. ~/Desktop/stage, issue the following zip command:
#comment: mention each file explicitly including all files in subdirectories with pathnames from the stage directory:
To find out all of the files that must be included in the zip command, from the ~/Desktop/stage directory, you can issue the following ls command before issuing the zip command below:
```

$ ls -R *

```

For example:
```

$ zip ../tmp.zip ./install.rdf ./chrome.manifest ./chrome/* ...

```
# comment: the use of the ellipsis, ..., substitutes in the example for  explicitly including all files in the subdirectories of the stage directory which you still must do - i.e. the ellipsis will not work.

The zip command creates the file, tmp.zip, in the ~/Desktop directory, but only if you explicitly included [highlight]ALL of the files in the stage directory[/highlight], i.e. not including the ellipsis!

Now that we have two files in ~/Desktop, tmp.xpi and tmp.zip, do an ls command to check the difference in the file sizes as follows: 
```

ls -lt tmp.*

```
The sizes should be different probably more than you thought, i.e. not by just a couple of bytes due to the different computer and zip executables on which the add-on was initially built.

Now, we go back to the subdirectory staged-xpis/*:
```

$ cd ~/.mozilla/firefox/*.default/extensions/staged-xpis/*

``` 
Note: <- don't forget the asterisk at the end of the line

Now we copy the tmp.zip file we created from the stage directory in ~/Desktop into the original filename, tmp.xpi by issuing the following command:
```

$ cp ~/Desktop/tmp.zip ./tmp.xpi

```

Note: the tmp.xpi file is just a zipped file upon which you can invoke unzip to inflate the files into the stage directory, as above, and then create tmp.zip eventually copying it into tmp.xpi

Now, cd to your /home/ubuntu directory:
```

$ cd

```
and [highlight]RESTART Firefox at this point[/highlight].

Upon restarting Firefox, you may get a notice saying that the add-on is incompatible like I have for Update Notifier in this example - however, I do have an icon in my status bar for it, and it does allow me to right-click and select Check for Updates. I just triggered it to check for updates, and I have two waiting to be updated!

Works for me - and that's all I want until the authors whom still haven't updated their add-ons that I like update the add-ons!

Caveat: This methodology/procedure might not work for all Firefox 2 add-ons!

-- Tom

P.S. I used the same methodology to investigate why the TSG Forums Menu was not working and gave the information to Ciberblade yesterday, so when he gets the time soon, he will likely get it fixed in short order - meanwhile, I do have a working TSG Forums Menu add-on that works for FF 3.0b5 in Ubuntu 8.04 LTS Hardy Heron - and I must say, I like the small colored icons to the left of the selections! The fix for the TSG Forums Menu was not as simple as in this example, and involved doing a comparison with the previous version.

P.P.S. At some point, I am going to either disable or remove the boolean which allows you to avoid the compatibility check - but, for now I'm leaving it in just in case I want to add more of the extensions I had in FF 2.0.0.14.

Reference: Original post by lotuseclat79 at Tech Support Guy UNIX/Linux Forum,  [http://forums.techguy.org/unix-linux/715379-how-get-firefox-2-add.html](http://forums.techguy.org/unix-linux/715379-how-get-firefox-2-add.html) ,  25-May-2008, 09:33 PM which has been slightly modified per K.Mandla instructions.

---

