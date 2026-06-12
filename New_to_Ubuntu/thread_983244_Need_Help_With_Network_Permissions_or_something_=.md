---
title: "Need Help With Network Permissions or something =/"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Ice Dragon on 2008-11-15
Hello all, ive been having little hinderances to my operating Ubuntu as my main OS on multiple computers and im hoping that at least this issue can be resolved as im sure its just a matter of me not understanding linux file permissions or network shares or something.

Here is the setup.

My at home Server is running Ubuntu 8.04 using Samba (got it through add/remove) to share and set simplistic permissions to each share.

I have a share called Upload, which I set for everyone to have access with read and write permissions and its visible.

I have another share called USB1TB which is my external Terrabyte drive with everyones data on it. I have that set to read only, people on the network can get files from it but in order to get files onto it, they must send it to the Upload folder and have the server administrator (me) copy it from Upload to USB1TB.

Now, my wife has windows xp and she can send files to the Upload folder np at all, never a hinderance there.

My laptop has Ubuntu 8.10 installed, when I send some files to Upload, it works, when I send other files it tells me different error messages depending on what file it was. The most recent one was a .zip file I downloaded and wanted to send to the Upload folder, it wouldent let me and said the following:

"Error while Copying

Files in the folder
"myfile.zip" cannot be handled because you do not have permissions to see them."

This file I downloaded from the internet right onto my desktop where it is currently located.

What am I doing wrong?


edit: It may also be important to know that I tried to map the network shares like I would in windows. Since in Ubuntu its done differently, I followed a guide I found on the net that told me to put:

"//server/usb1tb /media/usb1tb cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//server/upload /media/upload cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0"

into my /etc/fstab. I then created shortcuts on my desktop to /media/usb1tb and /media/upload. I thought it was working well, but maybe this has something to do with what is wrong. Thanks again!

---

### Post by Kellemora on 2008-11-15
Hi ID

Since you are running it as a server, it might be a little over my head here.

I'm running 8 computers here, only 3 are not Ubuntu machines.

For some reason, networking in Ubuntu has been a nightmare for me too!  Still gives me problems from time to time.

In my case, installing smbclient and removing smbfs pretty much cleared up most of our problems.  However, you may probably need smbfs is you are running a file server.

The reason I removed it was because if I ran smbtree without it installed, ALL of the shares showed up, with it installed, none of the Ubuntu machines would show up on the network except the host.

One other issue is that smb.conf is pretty much useless, except for using it to try and update the binary Samba configuration file located in /var/lib/samba.  It's not editable by humanoids!

I'm trying to run an office here and still have one glitch that we have NOT been able to get around yet, other than the method we are using.  This IS going to sound ODD, it could be a BUG, I don't know.  But to move files around from place to place, we CANNOT PUT those files on another machine or hard drive, we can only GET files from other machines.

That might not make sense, so let me word it this way.
If you are at machine A and want the file on machine B, DO NOT, while at machine A, put the file onto machine B.  Instead, put the file in the shared folder on machine A, THEN got to machine B and fetch the file from machine A from machine B.
This way, the file keeps ALL of it's original permissions when placed on machine B!
If machine B is where we STORE the files for use during the day, anyone can draw them from this machine no problem.
However, if we PUT the file from machine A directly onto machine B from machine A, then nobody and no one has permission to edit those files.  Makes it rough to keep client data up to date when it don't work right.

I'm working on a Cron job that will fetch the files from each workstation and Sync them with machine they will be drawn from by the other users of that file.  I haven't got it perfected yet and was hoping that the problems with networking would be solved before they issued a new release.  Seems they only went from bad to worse to me!

We have one machine that drives us nuts, first it's there, then it isn't.  Jump through flaming hoops and hopefully get it up and running again, then the next day it's down again.  

The problems with this machine is what taught me that the smb.conf file has little to nothing to do with file sharing.  The actual file doing it, as I mentioned earlier is found in /var/lib/samba and it's an uneditable binary file.

However, the illogical trick I'm using to get things working is actually fairly simple.  Three boots within a short time frame.
Boot #1 reads the var/lib/samba configuration file.
If you boot again, Samba must say, hmmmmm, why is he doing that, maybe I should look at smb.conf for once.  So it does and boots up how the smb.conf is edited.
But if you wait, the next boot will be from the /var/lib/samba folder so you're back to square one again.  That old file was not overwritten.
However, if you do your 3rd boot-up in a timely fashion, the currently read smb.conf must be converted to binary and written to the /var/lib/samba configuration file.
I think I can safely assume that is what's happening, because if I edit the smb.conf file and reboot three times, it will work just fine after that, for about 3 to 4 weeks or until the next automatic update comes down the pike.  Then we start over again trying to get all the networking back up and running again.

I had mentioned this to others, some said I was crazy as a loon, but a great deal of others said Hey Thanks, that worked!

If you can type smbtree into a terminal and see ALL your shares, but one of your drives or machines are not showing up under Places Network, just try booting that machine three times without changing anything and see if it don't fix itself.  It does for us QUITE OFTEN.............

Good Luck

TTUL
Gary

---

### Post by Iowan on 2008-11-15
Check the owner/permissions on that downloaded file - if it kept original settings, you may need to "chown" them before it'll play nice.

---

