---
title: "New Install - A Few Questions"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by mgbolts on 2008-09-15
Hi,

Apologies in advance if the answers already exist. I have spent many hours fixing some issues to get this far (a fried memory stick killed a few hours too!).  I am new to UNIX and have a new install of Ubuntu AMD64(? I think).

Works great, very impressed with the platform! Appear to have got Webmin and Samba running, impressed myself. 

Some niggling issues:

1. Couldn't get Sun java plugin working at first, installed ICEDTEA instead, seems to work. Still cant get the webmin file manager to work, just comes up a grey screen.  Before I installed Icedtea, it would say it needed java. Any ideas?

2. Trying to get access to files on server from windows PC. Created a folder /mnt/public. Made a bunch of changes in Samba. I can see it on the server and also the windows pc but dont appear to have permissions for either.

Your assistance would be appreciated.

---

### Post by porchrat on 2008-09-15
As far as accessing the ubuntu samba share from a windows PC...do you have firewalls up?  Firewalls will generally cause havoc with samba shares.

You also need to be a little more specific, what happens when you try to access the share folder from the windows PC?

---

### Post by mgbolts on 2008-09-15
Thanks,  Not that I am aware of. Except maybe on the router, I have a D-link home wireless router which everthing goes through, the server is hardwired and PC is wireless.

---

### Post by Bucky Ball on 2008-09-15
1/ Go to Synaptics Package Manager (System->Administration) and search for:

ubuntu-restricted-extras

Tick it and apply changes - there's your java.

2/

a/ Windoze - just right click on the partition/folder/file then Share and allow others to read and write in the setup there.

b/ Ubuntu - create a share folder on the desktop (or an existing folder) then right click/Share Options and take it from there. If it asks you to download anything, agree. You don't really need to set up a samba server as such in Hardy. The last step of this you should be asked it you want samba to change permissions on the folder for you. Agree. Log out of Ubuntu and in again. Done.

Places/ Network/ Windows Network and you should see your windoze shared partitions/folders. 
You should see your Ubuntu shared  things in the network window under their name (not in windows network).

* Important - make sure everything in both systems is in the same domain; eg

In Ubuntu, System-->Admin-> network -> general. 

Name: UbuntuBox (or whatever)
Domain: Home (or whatever)

Make sure domain same as Windoze box.

Hope that helps. :)

* Let us know what happens, as mentioned above - be as specific as you can. When you are asked for a password on the Windoze box, enter the details of you Ubuntu system - that is where you are trying to access the file.

---

### Post by mgbolts on 2008-09-15
Thanks for your help

1. Took  a while to download.  I have installed the new 'packages'.  Quit firefox, and opened again. Looked in plugins and and Sun Java is not on list. Do I need to uninstall Icedtea first?

2. Getting there, slowly. Will get back to you shortly.

Cheers

---

### Post by mgbolts on 2008-09-15
2. I have got this working for a folder created on the desktop and then 'enabled' in samba. I have tested it with add/deletes both ways, seems good. Thank you for that!

---

### Post by Bucky Ball on 2008-09-15
1/ From synaptics description:

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (gstreamer plugins), Microsoft fonts,
**Java runtime environment**, Flash plugin, LAME (to create compressed audio files),
and DVD playback.

2/ :)

---

### Post by mgbolts on 2008-09-15
Ok, enough for one day. Thanks once again.

Cheers Mate

---

