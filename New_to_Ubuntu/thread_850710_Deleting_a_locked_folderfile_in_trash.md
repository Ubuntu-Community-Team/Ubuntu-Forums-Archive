---
title: "Deleting a locked folder/file in trash"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by scotcella on 2008-07-05
Hi all,

I am trying to empty my trash can, and there are a bunch of pictures in there that appears to be locked. It won't allow me to delete them cos the pictures are locked. 

How do I empty the trash can when these pictures have a pad lock on them?

Many thanks in advance!

---

### Post by drs305 on 2008-07-05
Substitute your username in the command below:

```
sudo chown -R *username* ~/.local/share/Trash/files
rm -r ~/.local/share/Trash/files
```

This can be done with one command but this way is safer...

---

### Post by CAE2685 on 2008-07-05
For anyone who would prefer a graphical approach:

Open a terminal and type 
```
sudo nautilus
``` and type in your password.

:!:**Be very careful. You just opened the file explorer as the root user, you can delete anything.**

Navigate to the trash folder, and delete the files from there. Exit Nautilus.

---

### Post by vistasucksss on 2008-07-07
i am having the same problem and when i navigate to the trash folder in root.. the window fades to gray and i am unable to do anything... anybody know whats going on?


-chris

---

### Post by bumanie on 2008-07-07
Try navigating there following terminal command > gksudo nautilus You can often delete locked files in this mode.

---

### Post by vistasucksss on 2008-07-07
hey bumanie

thanks ill give it a try :)

---

### Post by vistasucksss on 2008-07-07
just tried it that way as well and got the same result - the window was 'not responding' when i navigated to trash....

---

### Post by vistasucksss on 2008-07-07
my computer actually just froze.. had to reboot...

just want to delete these files from the trash!

tried drs305's suggestion also but still no luck...

does anybody have a solution to this??

best and thanks
-chris

---

### Post by Shazaam on 2008-07-07
> **vistasucksss said:**
> i am having the same problem and when i navigate to the trash folder in root.. the window fades to gray and i am unable to do anything... anybody know whats going on?


-chris

Turn off desktop effects and try gksudo nautilus again.

---

### Post by vistasucksss on 2008-07-07
girls@girls-desktop:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:6148): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


that is what i get when i type that....

and when i navigate to trash it just has a 'waiting' mouse icon...

thanks anyway though i dont know what to do... i recently installed cairo dock? could this be anything?? i did close that out though the last time i tried...

---

### Post by bumanie on 2008-07-07
In Gutsy the code is
> sudo rm -rf /home/yourusername/.Trash/*

In Hardy the code is
> sudo rm -rf /home/yourusername/.local/share/Trash/files/*
 This will definitely work, but it is very powerful, make sure you are deleting the correct thing.
Just to add, I had a similar problem with a friends computer the other night. Something seemed to have partially taken over the computer and the hard drive was being caned real bad. Click on this file, try to delete it and the hard drive would go crazy and the computer would barely run. The above command was the only thing which would get rid of it.

---

### Post by vistasucksss on 2008-07-07
girls@girls-desktop:~$ 


sorry but where it says 'yournamehere'  would i just put 'girls' because thats what i put and it didnt work... :/

---

### Post by vistasucksss on 2008-07-07
oh wait.. the trash can is empty now.. ok thanks everyone!

---

### Post by scotcella on 2008-07-07
> **vistasucksss said:**
> oh wait.. the trash can is empty now.. ok thanks everyone!

Had the same issues as you- freezing, fading etc etc, the last one helped me..whew.. I thought I was never gonna get rid of the files I wanted gone!

---

### Post by webofunni on 2008-07-07
> **vistasucksss said:**
> girls@girls-desktop:~$ 


sorry but where it says 'yournamehere'  would i just put 'girls' because thats what i put and it didnt work... :/

```
whoami
```

Will give "yournamehere" ;-)

---

### Post by grim4593 on 2008-07-07
That is nice and all to use sudo to delete the file from the trash, however, that is not ideal. How would a non-admin user fix this problem?

How could something that was able to be moved to the trash not be able to be deleted from the trash due to permissions?

---

### Post by webofunni on 2008-07-07
> **grim4593 said:**
> That is nice and all to use sudo to delete the file from the trash, however, that is not ideal. How would a non-admin user fix this problem?

How could something that was able to be moved to the trash not be able to be deleted from the trash due to permissions?

The force option in rm < ie rm -f > will remove the files forcefully and the files under the trash are owned by the user itself so there is no need of sudo ;-)

---

### Post by kamitsukai on 2008-07-07
this must be some type of bug as i get it too...

---

### Post by ibuclaw on 2008-07-07
Not having write permissions to a file is not a bug.

Infact, it makes perfect sense that you can't remove it ;)

try out this
```
mkdir -p ~/Desktop/DIRONE/DIRTWO
touch ~/Desktop/DIRONE/DIRTWO/FILEONE
chmod -w ~/DIRONE/DIRTWO

```
Then move the folder on your desktop to trash.
You'll find that you won't be able to empty it because the absence of write permissions deny you the right to.

In future run this command:
```
sudo chmod +w ~/.local/share/Trash/files/* -R
```
And then empty the trash.

Regards
Iain

---

### Post by scotcella on 2008-07-07
> **grim4593 said:**
> That is nice and all to use sudo to delete the file from the trash, however, that is not ideal. How would a non-admin user fix this problem?

How could something that was able to be moved to the trash not be able to be deleted from the trash due to permissions?

Be assured.......Of course i wouldn't reccomend a newbie to use this. I asked because I needed to get rid of some locked files that were photos that I didn't need on my laptop anymore- they were copied and pasted from a CD I made and thus when it was pasted onto the laptop it was in read only mode. I made the mistake doing that and thus couldn't get rid of it.

NOTE to newbies: Stay far far away from this... until you've gained a better understanding how your desktop is set up and works and you've got a better understanding of the power of your terminal has at your command!

---

### Post by grim4593 on 2008-07-08
I understand why the problem occurred. I have had the same problem many times in the past. However, I don't think command-line-fu is a solution for something as trivial as emptying the trash. You'd think that the "Empty Trash" button would jump through the hoops to remove everything in the trash folder so the user wouldn't have to.

Not having write permissions is a null argument. The user clearly doesn't want the files anymore if he/she moved them to the trash AND hit the empty button. Maybe a solution would be to set the write bit when the files are deleted from the trash.

---

### Post by scotcella on 2008-07-09
Hmm not sure what you mean fully by your post, but I'll try answer you the best I can with your points- just to make sure I'm on the same wave length :o)

> You'd think that the "Empty Trash" button would jump through the hoops to remove everything in the trash folder so the user wouldn't have to....

.........The user clearly doesn't want the files anymore if he/she moved them to the trash AND hit the empty button. 

I did and an error came up that I didn't have permission and those locked files stayed in the trash. Those that were not locked were gone without any troubles. I looked at my original post and I can see that I didn't explain this part then.

> 
Maybe a solution would be to set the write bit when the files are deleted from the trash.

Not sure what you mean by this, can you elaborate a little?

---

### Post by grim4593 on 2008-07-09
Well typically when a user hits "Empty Trash" they expect the trash to be emptied. Currently, if there are write protected folders in the trash, those files will not get removed. My suggestion is to apply write permissions (chmod +w) to the write protected files so the Trash can be emptied correctly behind the scenes. The user doen't have to drop to a terminal to clean the trash manually (why bother having a GUI trash applet if it can't empty the trash?). Otherwise the write protected files do not disappear as expected, there is no "permissions" error popup, the files continue to take up space, and confuse users.

---

### Post by ububaba on 2008-07-10
[HTML]sudo rm -rf /home/myname/.local/share/Trash/files/* [/HTML]
I used the above, a "root-File Browser" which is totally blank
has opened. For last half an hour it has been waiting and waiting.
I have made several attempts without success.

---

### Post by drs305 on 2008-07-10
> **ububaba said:**
> [HTML]sudo rm -rf /home/myname/.local/share/Trash/files/* [/HTML]
I used the above, a "root-File Browser" which is totally blank
has opened. For last half an hour it has been waiting and waiting.
I have made several attempts without success.

Did you substitute your log-on name for "myname"? The command should be run from the command line and should not be opening any browser. It should ask for your password and then after completing the command return to a normal prompt.

You might try omitting the "files/*" ending and see if you get the same results. Be careful - 'sudo rm' can be a very dangerous command if you don't use the correct path!

---

### Post by ububaba on 2008-07-10
> **drs305 said:**
> Did you substitute your log-on name for "myname"? The command should be run from the command line and should not be opening any browser. It should ask for your password and then after completing the command return to a normal prompt.

You might try omitting the "files/*" ending and see if you get the same results. Be careful - 'sudo rm' can be a very dangerous command if you don't use the correct path!

I did use the log-in name. That was not a problem. Soon I'll try to do 
away with "files/*" and see what happens.

---

### Post by drs305 on 2008-07-10
> **ububaba said:**
> I did use the log-in name. That was not a problem. Soon I'll try to do 
away with "files/*" and see what happens.

I just threw that in as an afterthought - it shouldn't really make a difference unless the * wildcard was doing strange things.

---

### Post by jomabo on 2008-09-09
(1) I saw the exchange about locked files in the trash. Now that I know how to delete them, I am even more curious to know how they ended up that way. Could someone explain the "why" of files becoming locked--or, if there is a place to find this kind of information about Ubuntu 8, just tell me where that is.  

(2) Also, when I switched from XP to Ubuntu 8 from a defective system file crash, I ended up with a locked file. I think it has the doc, pdf and midi file that were on the harddrive.  Is there any way to get into such a file and "lint pick" (if there are coherent pieces left)?  Again, if this information is already somewhere on the Ubuntu site, please just give me a link.

Thanks!

---

### Post by Cariboo1938 on 2008-10-26
> **drs305 said:**
> Substitute your username in the command below:

```
sudo chown -R *username* ~/.local/share/Trash/files
rm -r ~/.local/share/Trash/files
```

This can be done with one command but this way is safer...

I also have this Trash issue.
I followed drs305´s instructions and I still have two directories shown by clicking the Trash icon with their names (Music, Pictures) or 
in the terminal with the command line ´ls -al´ 
[email]root@karibu-desktop:~/.loca[/email]l/share/Trash/files# ls -al
total 8
drwxrwxrw- 2 root   karibu 4096 2008-10-26 10:54 .
drwxrwxrw- 4 karibu karibu 4096 2008-10-13 21:40 ..

as dots! Originally they both where owned by karibu but I changed ´one dot´ to owner root.

what is to do, to empty the Trash totally :confused:

---

### Post by drs305 on 2008-10-26
Open nautilus with the following command. Select/highlight the 'Trash' folder and SHIFT-DELETE (holding down the SHIFT and DELETE keys at the same time):
```
gksu nautilus $HOME/.local/share
```

This action will delete the Trash folder and the 'info' and 'files' subfolders. They will be recreated the next time you delete something.

---

