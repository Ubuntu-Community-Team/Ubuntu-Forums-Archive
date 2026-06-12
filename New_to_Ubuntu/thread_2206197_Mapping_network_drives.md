---
title: "Mapping network drives"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by dave93 on 2014-02-17
I am trying to set up some Linux boxes (13.10) at work.
I have managed to mount 2 shared drives fairly easily but then I cannot seem to add any more.

My fstab entries look like this:

//192.168.1.116/public /media/I_drive cifs credentials=/home/knightmayre/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

//192.168.1.101/c /media/J_drive cifs credentials=/home/knightmayre/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

//192.168.56.60/scanner /media/S_drive cifs credentials=/home/knightmayre/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

I_drive and J_drive have no issues, but the 3rd entry gives me a weird error message:

mount: only root can mount //192.168.56.60/scanner on /media/S_drive

I can ping the machine fine, just can't mount it. I have stared and stared at this and can't see anything wrong.
Any assistance would be greatly appreciated!

---

### Post by TheFu on 2014-02-17
I'd try to mount it manually in a terminal and turn the verbosity WAY UP to see the issue.  Could that other box use newer authentication?
Can you browse to that share using Nautilus?

---

### Post by dave93 on 2014-02-17
No, I can't get access to that share at all... Windoze boxes have no issues, straight in.
I did a NET USE to get the full path of the shares but no luck, even just using smb://IPAddress/ShareName (don't know how to get that into verbose mode)

I know I must be doing something wrong but I have no idea what lol

---

### Post by Bucky Ball on 2014-02-17
Could be off the ball but,

//192.168.56.60/scanner /media/S_drive cifs credentials=/home/knightmayre/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

There is a space between 'scanner' and '/media'. Should that be there? Also, can you try mounting it manually with:

sudo mount -a

? (or the specific path to the partition/folder).

---

### Post by dave93 on 2014-02-17
Thanks for the reply but there is also a space before /media on the 1st 2 working entries. :)

I run sudo mount -a when I make changes to fstab but now I'm getting a permission denied error which hasn't happened before.

edit: when I re-add the 3rd line I get a popup saying "S_drive has been connected" but I cannot access it (same error as on first post).

---

### Post by Bucky Ball on 2014-02-17
Removed duplicate post. ;)

I see the spaces now, yes.

---

### Post by dave93 on 2014-02-17
Thanks, I was trying to remove it myself

Progress:
//192.168.56.60/scanner /home/testing cifs username=xxxxx,password=xxxxx,uid=1000 0 0

That line works, all I do is go into the folder called testing & everything I need is in there.
All I need to do now is to get it to go to smbcredentials to get my user credentials rather than read it in plain text in fstab.

---

### Post by TheFu on 2014-02-17
They could be using AD+Kerberos for authentication.

Does **smbclient** or a manual **mount** command work provide better diagnostics?  Dump the GUI, but we need some log messages.   **smbtree** is another useful cmd for diagnosing stuff like this.  RTFM to the detailed options and how to turn up the messages (verbosity).

---

### Post by dave93 on 2014-02-18
No, we only have 1 server using AD and that's not part of the network that I am trying to access.
I discovered that it was a permissions issue, think it was trying to use the wrong credentials.

I amended my fstab file to look like this and it works, although drive Z is incredibly slow when compared to a Windoze box accessing the sane folder.

//192.168.1.116/public /media/I_drive cifs credentials=/home/knightmayre/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

//192.168.1.101/c /media/J_drive cifs credentials=/home/knightmayre/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

//192.168.56.60/scanner /media/S_drive cifs username=myusername,password=mypassword,uid=1000 0 0

//192.168.16.114/Drive_Z/Backup /media/Z_drive cifs username=username,password=password,domain=domainname,uid=1000 0 0

I had to create a new user on the machine that hosts Drive_Z and once I put that info into fstab, it works! :)

Any ideas why the Z drive is so slow? It takes minutes to open a large folder. 
But I'm happy I made progress as I didn't have a clue what TheFu was on about. lol

Cheers

---

### Post by TheFu on 2014-02-19
/etc/fstab is a world readable file. Just sayin'.

Those tools are used from a terminal.
Those tools have "verbosity" options that can be enabled.
The output from those tools when verbosity is enabled will provide information about any failures.
With the information, it is possible to determine the exact issue. No more trial and error techniques.

That is all.

---

