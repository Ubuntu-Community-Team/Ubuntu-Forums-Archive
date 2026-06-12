---
title: "HowTo: Vangogh Desktop [Server Edt Soon]"
date: 2006-07-05
forum: Outdated Tutorials &amp; Tips
---

### Post by noob_Lance on 2006-07-05
Hey,

Well Your probally asking yourself... what the h3ll is "Vangogh" and why is it in the how to section! Vangogh Is Eye Candy ^_^


After Countless Searching And Not finding anything i wanted. I decided to take it upon myself to do something a little more... a little interesting. My original idea came from my thoughts of setting up a server and wanting to have a little fun with it. something most servers never really see. Its all things that go on in the background. Now Ive made something for the foreground. 

SO anyways.. on to what Vangogh Is! It is a program that will rotate your desktop image every 2 minutes (soon to be a user set argument, defaut 2min)
But the one thing i really wanted it to do was have a sort of profile system. So if you have difference users.. or just different tastes (like myself) you can run the app with a different preference.

Anyways!. On to how to get it to work and then how to install it...:eek: 
*note- gnome friendly only atm. kde comming soon.

```

lance@davinci:~$ vangogh
vangogh [-u] [-p] [-c] [-d] [-e]
        [-u] %p         The Profile To Update
        [-p] %p %t      The Profile To Be Loaded
                %t      The Time (in seconds) to Sleep the Program
        [-c] %n %d      To Create a Profile
                %n      The Name Of the New Profile
                %d      The Directory To be used for the profile
        [-d] %p         The Name Of the Profile To Delete
        [-e]            To Kill The Program



```


I will show you an example of one i used myself.
```

lance@davinci:~$ vangogh -c Abstract /home/lance/wallpapers/
profile Abstract created successfully!
lance@davinci:~$ 

```
We Just created a profile called *Abstract* using the folder */home/lance/wallpapers*

Next to start the program with our new profile:
```

lance@davinci:~$ vangogh -p Abstract
profile loaded successfully!
lance@davinci:~$ 

```

Now To Delete a profile:
```

lance@davinci:~$ vangogh -d Abstract
Profile Deleted Successfully!
lance@davinci:~$ 

```


Ok now that we ran through the basics... now to installing the program. 
Download the file uploaded below. unzip to your desktop and then open a terminal.

```

cd Desktop/
sudo cp vangogh /usr/local/bin

```


I would attach screen shots... but well its useless lol. theres nothing to see except the background lol


Now your ready to rock and roll. Mind you this is the desktop version. Server Edition will be comming soon (as soon as i move and buy a computer for a server) I will get cracking on that. 



Any questions. Please Just Ask. Im looking for someone who can program a GUI for some spesific parts. If anyone is willing.. please email me (msn prefered) at silver_suicide_rider [at] hotmail.com

Regards
~Lance

---

