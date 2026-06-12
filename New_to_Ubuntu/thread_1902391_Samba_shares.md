---
title: "Samba shares"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by oakridge on 2011-12-30
I have just installed Ubuntu after using Mandrake/Mandriva since Version 7, but 2011 Spring is proving to be a bit of a pain.
 
The Ubuntu Desktop 11.10 installation went very well, but it is certainly very different to Mandriva.
 
Right, down to it. I need to access MS PCs - XP and 7. I have installed Samba, but when I go 'Network' 'Wokgroup' comes up but then I get an error; 'Failed to receive share list from server'.
 
The BT HomeHub 3 recognises the Ubuntu machine and asigns the IP address of 192.168.1.66, which is in the right range. The Windows machines do not list the Ubuntu and nor does BT Desktop Help.
 
Thank you in advance.
 
Malcolm

---

### Post by oakridge on 2011-12-31
Just a further note I can ping any of the Windows machines from Ubuntu by IP address and vice-versa, but not by name.

I have just noticed that I have given this machine the name oakridge-unbuntu, perhaps I have offended it.

Malcolm

---

### Post by Morbius1 on 2011-12-31
>  I have just noticed that I have given this machine the name oakridge-unbuntu, perhaps I have offended it.You haven't offended it but it is invisable to the network because it's 1 character too long.

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - right uner the workgroup line:
```
netbios name = oakridge-ubuntu
```[COLOR=Blue]*It doesn't have to be that exact name but it must be 15 characters or less in length.*[/COLOR]

While you are in the you might want to add another line right underneath the previous one:
```
name resolve order = bcast host lmhosts wins
```Then save smb.conf and restart samba:
```
sudo service smbd restart
``````
sudo service nmbd restart
```

---

### Post by oakridge on 2011-12-31
Thank you Morbius1 for your reply.  I will do as you suggest.
 
Since my last post I have installed PyNeighbourhood and I can now connect to most of the PCs.  I just need to persuade Microsoft to return the compliment.
 
Malcolm

---

### Post by oakridge on 2011-12-31
The first line generated an error:

:~$ gksu gedit /etc/samba/smb.conf

(gksu:3484): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

 but it did let me save smb.conf, phew.  

Now I want to copy files from one of the Windows 7 machines so how do I get a split second window in the KDE Dolphin/Internet Explorer application please?

Malcolm

---

### Post by oakridge on 2012-01-02
Now that I am beginning to find my way around Ubuntu and its interpretation of Gnome I have been able to do some further investigation.

pyNeighbourhoud finds the four PCs turned on at present, including the Linux but only finds the shares on two of them, including the Linux.  Windows finds all shares.

The 'Home' window finds Windows Network/Workgroup but then reports 'Unable to Mount Location, Failed to Retrieve Share List from Server'.

On Personal File Sharing Preference the 'Share Files Over the Network' option reports: 'This function cannot be enabled because the required packages are not installed on your system'.  It does not tell me what the required packages are.

The router (BT HomeHub 3) lists all computers and correctly reports which are connected or not.  The IP address given by the router is confirmed by ifconfig.

BT Desktop Help, which of course will only run on Windows machines, finds everything connected except the Unbuntu.

Windows Explorer finds connected computers and shares.

So that is it then in a rather large nutshell.  There are many features of Linux which I prefer over Windows so I really do not want give it up and anyway it is a challenge.

Malcolm

---

### Post by oakridge on 2012-01-04
Oh, woe is me, I have managed to do the most stupid thing; with great skill I have managed to delete all the text from smb.conf.   Is there a copy of it somewhere that I can download?

I cannot believe that I have made such an elementary mistake.  I was having trouble with Samba Server Configuration program which just did not seem to work.

Malcolm

---

### Post by Morbius1 on 2012-01-04
There is a copy of the factory fresh smb.conf at the following location put there just for people like us:

/usr/share/samba/smb.conf

It does have one curious mistake in it. It has the following line in it:
>                               encrypt passwords = **[COLOR=Blue]false[/COLOR]**                      [COLOR=Blue]*It could also list it as No*[/COLOR]
That should be changed to true or yes.

---

### Post by oakridge on 2012-01-04
Bingo, yippeee, it works.  Thank you all for your help.

Malcolm

---

### Post by audiomick on 2012-01-04
Hallo Oakridge. You might want to have a look here

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Two of the points there have been covered, but it is a good place to know about if you have Samba problems.

---

### Post by Morbius1 on 2012-01-04
> **audiomick said:**
> Hallo Oakridge. You might want to have a look here

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Two of the points there have been covered, but it is a good place to know about if you have Samba problems.
And I would point out that that HowTo never stipulates that the netbios name must be 15 characters or less in length and that bcast should appear first in "name resolve order". In fact he has it at the end not the beginning. And don't get me started on winbind :wink:

---

### Post by audiomick on 2012-01-04
> **Morbius1 said:**
> In fact he has it at the end not the beginning.

No he doesn't
The suggested order is this
>  name resolve order = lmhosts wins bcast [COLOR=Red]host[/COLOR]bcast is at the end in the default file. If I remember correctly, the relevant point in this change was the position of "host" in the list. Otherwise the "search assistant" that some providers had started using would get in the way of samba looking for the shares.

Why should bcast be at the start of the list?

I wouldn't dream of starting on winbind, as I know nothing about it. :)

---

### Post by Morbius1 on 2012-01-04
>  Why should bcast be at the start of the list?Let's look at all of the options available to "name resolve order". For a typical home lan that gets it's ip address via dhcp from their router "host" ( i.e., the hosts file ) isn't set up with the ip address and host names of all the other members of the lan, lmhosts doesn't exist, and wins refers to a wins server which doesn't exist on the network unless you follow a procedure to create one. The only one that works by default is bcast so put it first. The system will get "stuck" at wins unless you you move it as far away from the front of the list as possible.

---

### Post by audiomick on 2012-01-04
Ok, that seems fair enough.

The reason for putting "host" on the end was to stop a "service" some internet providers had started to use from interfering with finding the shares. I don't remember the details; it is more than 2 years since I looked into that. It is the one where if the browser can't find something, a "suggestions page" from the provider appears.

---

### Post by Morbius1 on 2012-01-04
I believe your confusing "host" with "wins". The phenomenon you are referring to I think is called "DNS Redirect". For some users who run the  command **smbtree** to get a list of the hosts and their shares and who do not have bcast first will get one of 2 error messages:
>  cli_start_connection: failed to connect to SOME-HOST-NAME<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFULAnd some of them will actually get something like this:
>  cli_start_connection: failed to connect to SOME-HOST-NAME<20> ([FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2]207.69.188.196[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]). Error NT_STATUS_UNSUCCESSFULThe last one ( [FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2]207.69.188.196 ) is the ip address of the users isp's dns server. The system has actually left the lan in a valiant effort to to try to resolve a host name to an ip address on the lan.

In both cases putting bcast first and putting wins at the end would be my suggestion for a fix.
[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by oakridge on 2012-01-04
Thank you for both of those suggestions audiomick, they will help my rusty old brain get back into gear.

Malcolm

---

### Post by oakridge on 2012-02-16
I am sorry AudioMick I missed your reply so belated thanks.  All is working fine now.

Ubuntu is reliable and predictable and is working hard.

Thank you for your help all.

Malcolm

---

