---
title: "Download speed"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by ucal on 2008-05-06
I'm used to around 60-150 kb/sec on vista with a high of around 400 IIRC. Ubuntu gets in the thousands, which is nice, but its in bytes per second.  I'm having the most trouble with the add/remove programs downloading. Is there any way to speed this up?  Firefox is pretty spotty too.  Sometimes it is great, youtube videos downloading in the background while I download a game I want  to try out, and sometimes it stalls out on me.

---

### Post by phr0ze on 2008-05-06
Add/Remove can be spotty after a new release. Try this.

Go to System->Administration->Software Sources
Then click on the box that says 'Download from: United States (or whatever country)'. Select 'Other...'

A new window will appear. Click the 'Select Best Server' button.

Once you go through this process your speeds should be better. It doesn't hurt to run this again from time to time as the server speeds will get better or worse depending on local and internet conditions.

Thanks.
John

---

### Post by ucal on 2008-05-06
I just tried that, and it might work yet (I'm running the test again, just to be sure), but the first test told me that no suitable servers were found, and that I should check my internet connection.  Thanks though.

Also, are there any good alarm clock programs out there with MP3/OGG/whatever support?  Or alternatively, music players with alarm support.  I tried a few on sourceforge, but for the life of me, I can't figure out how to install this stuff.  That is one plus of vista, it has .exe s.

---

### Post by nowshining on 2008-05-06
linux is NOT windows, so don't expect it to be. .exe's are equiv to deb files and vis versa..

Some programs my need to be installed from source, and rem. don't foget the install the build-essential package.

installig from src is quite easy and sometimes even more easier than installing an exe filne.

Once u make to compile and if all is successfull u can use sudo checkinstall -D make install to make a deb file for backup incase u will have to re-install.

edit: however by default when u use sudo checkinstall the deb file and or files will be owned by root and the group root.

---

### Post by ucal on 2008-05-06
I know linux isn't windows.  I was just lamenting what appears to be the loss of a simpler feature (though I'm sure it isn't really simpler one I actually get the hang of linux).  Though that's the only part of your post that meant anything to me.  The rest was just gibberish (albeit, I know it was terminal related gibberish).  That's why installing is difficult for me.  Though I plan to correct that with some reading. 

Back to the download problem though.  Any ideas?

---

### Post by nowshining on 2008-05-06
src = source,

it means source code, u can change it? add/remove stuff, etc.. by editing if u know any programming or anyone who does, u can also compile to ur specific CPU for a bit of optimazion.

the build-essential package iinstalls many basic files,programs that u'll need when compiling a program.

compiling = turning that human readable code to machine code so the computer can understand the program and allow u to use the program.

checkinstall = a program that allows one to create deb files, rpm files, etc.. when installing a program.

checkinstall -D = the -D part is the option to create a DEB package, D = DEB

permissions = u can't delete any file and or program without the right pw and if it's root, ubuntu, etc.. use sudo instead of root directly and the checkinstall command uses sudo which auto putes the root as the owner of the file - basically.. 

the deb file will be in the unzipped src folder and u'll have to sudo nautilus, sudo dolphing (whichever u use) if u want the GUI part and to right-click and properties to change the permissions of the file.

or

u can do it in the command line with:

sudo chown -R username:username pathtofolder/file

change username to ur username and pathtofolder/file to the path of the deb file or just the root of the diectory containing the src and deb file and input ur pw, note when using sudo it asks for UR username pw, and it will NOT show as u type, so just type it normally and then hit the ENTER key.

---

