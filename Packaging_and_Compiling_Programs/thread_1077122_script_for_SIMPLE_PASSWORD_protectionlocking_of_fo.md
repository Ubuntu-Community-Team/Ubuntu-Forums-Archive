---
title: "script for SIMPLE PASSWORD protection/locking of folders"
date: 2009-02-22
forum: Packaging and Compiling Programs
---

### Post by macvr on 2009-02-22
hi all,
i had always wanted to password protect folders [WITH NO ENCRYPTION REQUIRED]within my own user account, something similar to the password prompt feature of gksu applications

[COLOR="Blue"]so i'v come up with this idea: and **it works...!!! **[/COLOR]
i'm able to password "lock" the desired folder and then access it only after the password prompt is successful... therefore preventing access to the folder for any other non administrative user 

this is what i'v come up with...

[COLOR="Green"]
WHAT THIS SCRIPT DOES IS:
when u launch the command , it prompts u for the ROOT password to open the folder , therefore only persons who know the root password can access the folder.
opens the folder , allows access to files 
and access to the folder is blocked AUTOMATICALLY on exiting the folder ,
so u need not worry about remembering to use the terminal to re-lock the folder[/COLOR]

**Step 1**:

first we change permissions for the folder which we want to protect
```
sudo chmod a-r [COLOR="Blue"]/path/to/folder[/COLOR]
```
u have to enter your root password, when prompted ,to run this command
also change the [COLOR="Blue"]/path/to/folder[/COLOR] according to your folder location u wish to lock

**Step 2**:
now to create the key!

create an empty file ,and name it as u wish but for this HOW-TO i'm using "protector"

```
$touch .PROTECTOR
```
the file is created in your home/user/ folder

if u cannot see the file, select "show hidden files" from the View menu or press Ctrl+H , now the file should be visible

**Step 3:**

open the file using the text editor and enter the following command>
```

gksu chmod +r [COLOR="Blue"]/path/to/folder[/COLOR];nautilus [COLOR="Blue"]/path/to/folder[/COLOR];sleep 1;sudo chmod a-r [COLOR="Blue"]/path/to/folder[/COLOR]
```


now save and exit

**Step 4:**

now right click the file > select "properties"> select "permissions" tab> check "Allow executing the file as program"

**Step 5:**

Create a launcher on the panel/or Desktop... select any name for the launcher
for the command section of the launcher enter: 
```
/home/user/.PROTECTOR
```
save and exit...


thats it...:D 

[COLOR="Green"]Now to access the protected folder, all u have to do is click the launcher and u have access to the folder after u enter the password :D[/COLOR]


ALTERNATIVELY instead of the launcher u could just run the file directly...


you can create separate launchers for individual folders in the similar way.:p

*Advantage & Disadvantages:* [depending on how u look at it ;)]
once u move out of the folder, it is locked, so to reopen folder u have to use the launcher again, in case this is frustrating, u can increase [COLOR="Red"]sleep[/COLOR] interval from 1 used here to any higher interval of your choice... 

now this works fine nothing wrong with changing permissions and blocking access

[COLOR="DarkRed"]:KS*********i need help getting this idea fully implemented , and perfected as a package*********:KS

1-as of now i use the gksu and the root password, but i would prefer if the prompt was for the user account password, i'd like to know how to do that
2-even better way is to create a nautilus plugin that does this, so that when the folder icon is clicked then the password prompt appears instead of using this launcher hack[/COLOR]




[COLOR="Red"]**PS:**before the gurus jump up and say that this is not the best effective way, to do it, all i want to say is , _i dont need encryption and so dont many regular **HOME** users_,we dont care so much for encryption, we just want to simply lock the folder ,preventing instant access and not have my files modified[/COLOR];)

---

### Post by mwillams73 on 2009-06-16
Thank you for understanding what so many of us actually want!!! I dont want to encrypt my folders either so ive been searching for some way for me to lock and password protect my porn folders so when my kids are visiting i dont have to woory about them looking in my XXX folder, now if answering my daughters question "daddy? whats triple x for? " was that easy id have it made !!

But seriously this actually seems to be a good way to do it, i really hope you figure out how to make it utilize nautilus so that when you click on the folder it prompts you for a password. Please let me know if you make any headway with this, and I'll see what i can do about directing some attention to your thread so anyone who doesnt want to encrypt can have a far easier way to lock their folder can implement it. Hopefully this will catch on cause ive tried the encryption route and it sucks , to many things to remember. But this is simple effective and almost elegant in its design, Thank you very much for this script, I'll see: what i can do about getting some people to look at it!! :D

---

### Post by aysiu on 2009-06-16
Not only is this method *not simple*, but I couldn't even get it to work.

I'll take encryption over this any day. With encryption, I don't need to use terminal commands or follow complicated instructions.

---

### Post by macvr on 2009-06-16
> **aysiu said:**
> Not only is this method *not simple*, but I couldn't even get it to work.

If you follow the instructions it works...

[COLOR="Blue"]PLEASE READ CAREFULLY[/COLOR]

[COLOR="Red"]the gksu command is supposed to be entered into the .protector file[/COLOR] and saved

and not as you have done!

Pls enter the command into the text file and retest the method.

[COLOR="DarkRed"]YOU are one of the admins, and i cant believe you have done such a simple mistake...
[/COLOR]
[COLOR="Navy"]the terminal needs to be used only once to change the permissions for the folder the first time[/COLOR]

i used the touch command just to make it simpler for the user instructions

after which the terminal doesnt have to be used.

Opening of the folder is done from the launcher!


The problem with encryption is it creates encrypted duplicates of the files... and i have to delete the original file. whereas here the original file is not modified

---

### Post by aysiu on 2009-06-16
Doh!

I can't follow instructions.

So it does work, after all. I still don't find it simple. I may have to click more times to use encryption, but I don't have to use the terminal.

---

### Post by macvr on 2009-06-16
> **aysiu said:**
> Doh!

I can't follow instructions.

So it does work, after all. I still don't find it simple. I may have to click more times to use encryption, but I don't have to use the terminal.
you seem to forget , that even the initial setup for the encryption does require some setup!


If only you had re-read the instructions, instead of taking screenshots.

You have your needs , other have theirs, what feels good for you isnt necessarily good for others! So you are entitled to your opinion. Lets just leave it at that. 

And let the users decide what they want. If they want they can use it ...

---

### Post by bigboy_pdb on 2009-06-16
> **macvr said:**
> 
[COLOR="DarkRed"]:KS*********i need help getting this idea fully implemented , and perfected as a package*********:KS


If you're planning on making this a package in any of the standard repositories, it won't (or at least shouldn't) be accepted for a number of reasons.

Assuming it actually worked, there'd be these reasons:
[LIST]
[*]It's not a good practice (there are better ways to do this such as having the folder belong to an alternate user)
[*]Only users that have permission to run sudo can use it
[*]It isn't automated (users have to follow a complicated set of instructions)
[*]It has security issues:
[LIST]
[*]Unnecessarily using root to change access to a file
[*]Users can still enter the folder and access its contents (running "cd /path/to/folder" in the terminal enters the file and a user can use a loop with a set of characters to figure out what's in there)
[/LIST]
[/LIST]

However, it doesn't protect the file contents. Users can re-add read permission themselves (no root access is required). Simply right click on the file, select "Properties", go to the "Permissions" tab, and you can change the permissions there (or you can do it in the command line). In the end, all you've done removed read access and mislead people to believe that they need administrative rights to access it.

> **macvr said:**
> 
[COLOR="Red"]**PS:**before the gurus jump up and say that this is not the best effective way, to do it, all i want to say is , _i dont need encryption and so dont many regular **HOME** users_,we dont care so much for encryption, we just want to simply lock the folder ,preventing instant access and not have my files modified[/COLOR];)


If you choose to use a bad practice within your system, that only person who that affects is you, but when you attempt to have other people use it, more knowledgeable people will comment because poorly informed/ignorant users aren't aware of the consequences. Also, you're making assumptions about what other people want.

It's a good idea, but you're going about it the wrong way.

---

### Post by aysiu on 2009-06-16
> **macvr said:**
> you seem to forget , that even the initial setup for the encryption does require some setup! No, I haven't forgotten.

I noted that there are extra clicks involved. It is a fully GUI-led setup process, though. No terminal commands or scripts are required to use TrueCrypt.

> If only you had re-read the instructions, instead of taking screenshots, you wouldnt have made a fool of yourself! One does not preclude the other. As you can see, I was able to take screenshots while following the directions properly.

> You have your needs , other have theirs, what feels good for you isnt necessarily good for others! So you are entitled to your opinion. Lets just leave it at that. And I have expressed my opinion. My opinion is that your method is not simple.

---

### Post by macvr on 2009-06-16
> **bigboy_pdb said:**
> If you're planning on making this a package in any of the standard repositories, it won't (or at least shouldn't) be accepted for a number of reasons.

Assuming it actually worked, there'd be these reasons:
[LIST]
[*]It's not a good practice (there are better ways to do this such as having the folder belong to an alternate user)
[*]Only users that have permission to run sudo can use it
[*]It isn't automated (users have to follow a complicated set of instructions)
[*]It has security issues:
[LIST]
[*]Unnecessarily using root to change access to a file
[*]Users can still enter the folder and access its contents (running "cd /path/to/folder" in the terminal enters the file and a user can use a loop with a set of characters to figure out what's in there)
[/LIST]
[/LIST]


It's a good idea, but you're going about it the wrong way.
It does work.! no need to assume, aysiu just was too hypocritical to even read! to his own misgivings!

I have myself realized all these concerns , in my first post itself i mention that the better way is to prompt for the user password...

I myself do not advocate packaging ,until these kinks are sorted out... For now this is just a hack , or maybe even just any idea that needs better implementation

I dont know how to implement such a behavior. I too dont like prompting for the root password... but i dont see any other alternative!

Hence i had asked for others help, to sort these issues...

[COLOR="Blue"]If you have any knowledge/ideas regarding getting this done properly, help would be appreciated...[/COLOR] :)

---

### Post by bigboy_pdb on 2009-06-16
> **macvr said:**
> [COLOR="DarkRed"]YOU are one of the admins, and i cant believe you have done such a simple mistake...
[/COLOR]

Any person can make a mistake. I can easily see anyone making a mistake when following those instructions.

> **macvr said:**
> 
You have your needs , other have theirs, what feels good for you isnt necessarily good for others! So you are entitled to your opinion. Lets just leave it at that. 


> **macvr said:**
> It does work.! no need to assume, aysiu just was too hypocritical to even read! to his own misgivings!

You'll get much further with this idea if give more thought to people's responses and if you're less contentious.

---

### Post by Bodsda on 2009-06-16
Sorry, maybe I missed something, I looked over the instructions briefly and although I'm sure they do work it is overly complicated for zero protection, allow me to address a few issues

[LIST]
[*]
**sudo timeout**
    By default there is a window of 5 minutes between sudo commands where a password will not be prompted for, so if you were to use sudo for anything, leave the computer and then someone trundles along and opens the file there will be no prompt.

[*]
**livecd**
    There is nothing stopping me from booting a livecd and mounting the media and reading the file, or just booting to a root shell from grub for that matter.

[*]
**Permissions are so much simpler**
    You have gone out of your way to  make it ask for a password prompt, why not just execute ```
sudo chmod a-rwx /path/to/file
``` that would remove read, write and execute permissions for everyone on that file, meaning you need sudo to view it.
[/LIST]

Regards,

Bodsda

p.s: @macvr: I find your attitude towards staff members to be disgusting, everyone makes mistakes.

---

### Post by macvr on 2009-06-16
> **bigboy_pdb said:**
> Any person can make a mistake. I can easily see anyone making a mistake when following those instructions.

You'll get much further with this idea if give more thought to people's responses and if you're less contentious.

To get more perspective, you need to understand that
The tone was continued from a different thread. Since that was the tone of his reply, it prompted my replies.... 

For an admin he was far too condescending , either should point to the problems with the code [as you have done] or provide the solution should be an ideal tone for an admin... you can only get perspective if you read the tone of his replies, continued from a previous thread.

JUST LEAVE THE AYSIU MATTER ALONE... i'm not interested in ridiculous show of strengths... and i do believe that this is not the forum.

[COLOR="Blue"]I wish to discuss only regarding the topic.

I accept that this is only a small hack.

I'm open to any suggestions.

And always willing to accept any suggestions towards implementing the idea in a proper manner.[/COLOR]

---

### Post by Bodsda on 2009-06-16
Ok, ive been thinking about this problem for a few minutes and think I have come up with a more secure way of doing it.... No wait... I was half way through writing this when I realized I was planning on writing an encryption program.

Ok, so after much deliberation my conclusion is that to my knowledge it would be extremely difficult if not impossible, to implement a password protection system with no encryption that cannot be beaten with the root password, the reason is that the passworded file has to be somewhere, fact. Without encryption the file can always be read by root unless somehow you could make the file run a script before opening, which to my knowledge is not possible. Therefore, you cannot hide from a simple ```
sudo cat /path/to/file/dont_read_me.txt
```

If any of what I have said is wrong, please enlighten me.

Regards,

Bodsda

---

### Post by macvr on 2009-06-16
> **Bodsda said:**
> 
[*]
**Permissions are so much simpler**
    You have gone out of your way to  make it ask for a password prompt, why not just execute ```
sudo chmod a-rwx /path/to/file
``` that would remove read, write and execute permissions for everyone on that file, meaning you need sudo to view it.

I hadnt considered this...I missed it completely! i was only thinking of a single user system! and hadnt consider multiple users and preventing their access!

The reason for me choosing to use gksu is :
it prompts with the modal window for the password.

But concerns will be raised over using the root password, as the already pointed out, using the root password will not be accepted for Ubuntu packaging...

So, is there a way to prompt via modal window the user password instead?
Or Creating a separate user group with a password? and assigning the permissions of that group to the folder?

---

### Post by JordyD on 2009-06-16
Why *not* use encryption? It's actually much simpler; it's all GUI.

Plus, if you use encryption instead of permissions, you can assure that even if another user is on your account, they can't open the file without the password.

---

### Post by Bodsda on 2009-06-16
> **JordyD said:**
> Why *not* use encryption? It's actually much simpler; it's all GUI.

Plus, if you use encryption instead of permissions, you can assure that even if another user is on your account, they can't open the file without the password.

Not using encryption is the whole point of this thread :)

> **macvr said:**
> I hadnt considered this...I missed it completely! i was only thinking of a single user system! and hadnt consider multiple users and preventing their access!

The reason for me choosing to use gksu is :
it prompts with the modal window for the password.

But concerns will be raised over using the root password, as the already pointed out, using the root password will not be accepted for Ubuntu packaging...

So, is there a way to prompt via modal window the user password instead?
Or Creating a separate user group with a password? and assigning the permissions of that group to the folder?

Short: yes, probably

Long: yes, probably, but its pointless as it cannot prevent the use of sudo to view the file, which is why so many people are recommending encryption.

---

### Post by JordyD on 2009-06-16
> **Bodsda said:**
> Not using encryption is the whole point of this thread :)

But what is the point in not using it? Just because you don't *need* something doesn't mean you have to go to great pains just not to use it, especially if it does your job better.

---

### Post by megamania on 2009-06-16
> **Bodsda said:**
> 
**Permissions are so much simpler**
    You have gone out of your way to  make it ask for a password prompt, why not just execute ```
sudo chmod a-rwx /path/to/file
``` that would remove read, write and execute permissions for everyone on that file, meaning you need sudo to view it.

In other words, to protect a folder from a "casual" user of your computer, 
- execute the chmod command above,
- create a launcher on your desktop with the command --> gksu nautilus /path/to/file

That's pretty simple. Thanks for the quick solution, Bodsda.

---

### Post by macvr on 2009-06-16
> **Bodsda said:**
> 
Ok, so after much deliberation my conclusion is that to my knowledge it would be extremely difficult if not impossible, to implement a password protection system with no encryption that cannot be beaten with the root password, the reason is that the passworded file has to be somewhere, fact.
If any of what I have said is wrong, please enlighten me.


You are correct, i dont believe there can be a way to prevent root access.

But the problems i had with encryption was, it created duplicates of the files and the decyrption, and the deletion of the base file...

My goal is to 
1: lock a folder within the user account, so that the user has to use passwords to open the folder.
2: root / admins accessing the file is not an issue. I dont mind if the root uses access it...

Basically my reasons for this is: several times I'v had to allow family/friends use my own user account, so this lock is just to prevent 3 person users from EASILY accessing private files. on inadvertently open bank statements within the folders... I want to be free to allow the guest user without worrying about my files being looked into.

---

### Post by Bodsda on 2009-06-16
> **macvr said:**
> You are correct, i dont believe there can be a way to prevent root access.

But the problems i had with encryption was, it created duplicates of the files and the decyrption, and the deletion of the base file...

My goal is to 
1: lock a folder within the user account, so that the user has to use passwords to open the folder.
2: root / admins accessing the file is not an issue. I dont mind if the root uses access it...

Basically my reasons for this is: several times I'v had to allow family/friends use my own user account, so this lock is just to prevent 3 person users from EASILY accessing private files. on inadvertently open bank statements within the folders... I want to be free to allow the guest user without worrying about my files being looked into.

Well, thats easy, just restrict user read permissions.
```
sudo chmod a-r /path/to/file
```

then only sudoers can access it

> **JordyD said:**
> But what is the point in not using it? Just because you don't *need* something doesn't mean you have to go to great pains just not to use it, especially if it does your job better.

Dunno, ask the OP, I'm on your side. :)

> **megamania said:**
> In other words, to protect a folder from a "casual" user of your computer, 
- execute the chmod command above,
- create a launcher on your desktop with the command --> gksu nautilus /path/to/file

That's pretty simple. Thanks for the quick solution, Bodsda.

Your welcome.

Regards,

Bodsda

---

### Post by macvr on 2009-06-16
> **megamania said:**
> In other words, to protect a folder from a "casual" user of your computer, 
- execute the chmod command above,
- create a launcher on your desktop with the command --> gksu nautilus /path/to/file

That's pretty simple. Thanks for the quick solution, Bodsda.

but if you use gksu nautilus alone, and create new files in the folder, the file will be created with root permissions.

and opening these files opens programs as root.

To prevent the file creation as root and use the files as the user... you need to do as in the first post.

---

### Post by Bodsda on 2009-06-16
> **macvr said:**
> but if you use gksu nautilus alone, and create new files in the folder, the file will be created with root permissions.

and opening these files opens programs as root.

To prevent the file creation as root and use the files as the user... you need to do as in the first post.

I dont think he is talking about creating them as root, I think the post you quoted meant he would create the file, then edit permissions then create a launcher to view said file, although he should replace nautilus with a text editor.

Regards,

Bodsda

---

### Post by macvr on 2009-06-16
> **Bodsda said:**
> Well, thats easy, just restrict user read permissions.
```
sudo chmod a-r /path/to/file
```


Again i hadnt used the "a" , since i hadnt thought of multiple users!

Thanx for reminding :)

I'll edit the first post.

---

### Post by swisstone198 on 2009-06-16
It is best to keep running things as root to a minimum, so you could setup another user, change owner on directory/files to that user, then use gksudo -u <userid> command to open them.

---

### Post by Bodsda on 2009-06-16
> **swisstone198 said:**
> It is best to keep running things as root to a minimum, so you could setup another user, change owner on directory/files to that user, then use gksudo -u <userid> command to open them.

Thats another possible solution yeah.

---

### Post by Bodsda on 2009-06-16
> **macvr said:**
> Again i hadnt used the "a" , since i hadnt thought of multiple users!

Thanx for reminding :)

I'll edit the first post.

erm.. your still completely over complicating the matter, you only need to a-r the text file, you dont need this cd in change perms cd out change perms create protect file etc etc etc gibberish, you are still using the sudo password to access the file.

---

### Post by macvr on 2009-06-16
> **swisstone198 said:**
> It is best to keep running things as root to a minimum, so you could setup another user, change owner on directory/files to that user, then use gksudo -u <userid> command to open them.

The script runs as root only for 2-4secs :)
IT just changes the permissions of the folder and during that fraction of a second the non-root nautilus window opens, once the user moves out of the window he has no access.

I thought of that but it needed user profile creation and disk space loss. while the present method achieves the same result.

Ideally i would like to prompt the user password, rather than the root... I'm not able to find a way to do this.

> **Bodsda said:**
> erm.. your still completely over complicating the matter, you only need to a-r the text file, you dont need this cd in change perms cd out change perms create protect file etc etc etc gibberish, you are still using the sudo password to access the file.

But the file will be viewable...! I want the whole folder unaccessible , so that the presence of the file itself is not known :)

---

### Post by swisstone198 on 2009-06-16
> **macvr said:**
> The script runs as root only for 2-4secs :)
I thought of that but it needed user profile creation and disk space loss. while the present method achieves the same result.



You won't see any disk loss, you don't even need to give him a home directory, so just one line in the passwd file.

---

### Post by Bodsda on 2009-06-16
> **macvr said:**
> 
But the file will be viewable...! I want the whole folder unaccessible , so that the presence of the file itself is not known :)

So just create the file as a hidden file by preceding the filename with a '.'

```
touch .you_cant_see_me.txt && sudo chmod a-r .you_cant_see_me.txt
```

> **swisstone198 said:**
> You would need root access to change the permissions so no need to worry.

Well, actually if you were on a single user system you dont need root access, you can remove your own read permissions yourself, assuming the file was created by you under ~/```
chmod u-r /path/to/file
```

Regards,

Bodsda

---

### Post by swisstone198 on 2009-06-16
> **Bodsda said:**
> 
Well, actually if you were on a single user system you dont need root access, you can remove your own read permissions yourself, assuming the file was created by you under ~/```
chmod u-r /path/to/file
```Regards,


I misunderstood your post and promptly removed the comment.

---

### Post by Bodsda on 2009-06-16
> **swisstone198 said:**
> I misunderstood your post and promptly removed the comment.

That'll be why had trouble quoting it :) no worries, ty

Regards,

Bodsda

---

### Post by macvr on 2009-06-16
> **Bodsda said:**
> So just create the file as a hidden file by preceding the filename with a '.'

```
touch .you_cant_see_me.txt && sudo chmod a-r .you_cant_see_me.txt
```
WOW, i was thinking more about my user setup!, i had show hidden files always on!
I hadn realized > I was not trying to do this for my setup alone!

 but still this makes the files viewable on crtl+h

> **Bodsda said:**
> Well, actually if you were on a single user system you dont need root access, you can remove your own read permissions yourself, assuming the file was created by you under ~/```
chmod u-r /path/to/file
```

Regards,

Bodsda

But then the password prompt wont appear :( 
That kinda seems cool :P

I think my basic idea of using the root permissions was not correct , but 

[COLOR="Blue"]Maybe something in terms of creating a new group and being able to access folders assigned to the group only by using a non-root password would be the way to go...[/COLOR]

any ideas, maybe even if you come up with an idea later , do chime in :)

---

### Post by Bodsda on 2009-06-16
> **macvr said:**
> WOW, i was thinking more about my user setup!, i had show hidden files always on!
I hadn realized > I was not trying to do this for my setup alone!

 but still this makes the files viewable on crtl+h



But then the password prompt wont appear :( 
That kinda seems cool :P

I think my basic idea of using the root permissions was not correct , but 

[COLOR="Blue"]Maybe something in terms of creating a new group and being able to access folders assigned to the group only by using a non-root password would be the way to go...[/COLOR]

any ideas, maybe even if you come up with an idea later , do chime in :)

I dont understand your reluctance to only allowing sudoers access to the file, because if you have a group who can access it via a password it means more work to view your files. Your original problem iirc was that you wanted to keep prying eyes away from your file. This achieves that by only allowing those who know the sudo password to access the file.

Regards,

Bodsda

---

### Post by macvr on 2009-06-16
> **Bodsda said:**
> I dont understand your reluctance to only allowing sudoers access to the file, because if you have a group who can access it via a password it means more work to view your files. Your original problem iirc was that you wanted to keep prying eyes away from your file. This achieves that by only allowing those who know the sudo password to access the file.
If i understood you correctly>the access by a sudo user is the present method, i dont have a problem with that.
but as several have pointed out this as bad behavior.that is mostly the reason this is being discouraged... :(

or if u meant root access via sudo?... if the file/folder is accessed only by as sudo then the program open as root, which breaks the themes, user settings.

I'm trying to find a way that would be acceptable as an ethical one...
I had virtually given up on this idea since i had this thought in feb, as i had not got any feedback since then.
 but was brought back due to comments from another thread!

I hope i find a solution for this or if someone comes up with a similar alternative... :)

---

### Post by geo909 on 2009-06-16
Hello,

congrats, this is a very nice and clever idea! But as you said it's just a hack and you shoudn't really try to make a package out of it. Also what you need is not really common. You are actually trying to lock folders and hide them from "yourself" (= your account).
 
I think the three things below (that were already discussed here as I see) cover the vast majority of the users who wish to hide some folders from everybody:

[LIST]
[*]Right use of permissions
[*]Creation of another "guest" user in the system 
[*]Use of encryption
[/LIST]

Anything more just complicate things. That said, I think your hack is great and it seems that you have found a clever solution to your issue.

---

### Post by bigboy_pdb on 2009-06-16
> **swisstone198 said:**
> It is best to keep running things as root to a minimum, so you could setup another user, change owner on directory/files to that user, then use gksudo -u <userid> command to open them.

That's exactly what I was talking about in my first post.

**This method does not work**:
```

sudo chmod a-rwx folder

```
(regardless of how you use chmod to change the file permissions)

Putting sudo in the front of chmod does not keep the owner of the folder from being able to view the contents. For someone else to view the contents he/she just has to run:
```

chomod u+rwx folder

```
(this can also be done in the "Permissions" tab under the file's "Properties")

In other words, **you can only hide a file/folder that is owned by you from other users who are using your account by changing the ownership of the file/folder.** Technically, since you no longer own the file/folder, it really isn't possible without encryption.

When I said that the method which was first posted doesn't work, this is what I was referring to.

This is a complete counter example:
```

user@comp:~$ mkdir temp
user@comp:~$ ls -ld temp
drwxr-xr-x 2 user user 4096 2009-06-16 22:20 temp
user@comp:~$ sudo chmod a-rwx temp
user@comp:~$ ls -ld temp
d--------- 2 user user 4096 2009-06-16 22:20 temp
user@comp:~$ cd temp
bash: cd: temp: Permission denied
user@comp:~$ ls temp
ls: cannot open directory temp: Permission denied
user@comp:~$ chmod u+rwx temp
user@comp:~$ ls -ld temp
drwx------ 2 dave dave 4096 2009-06-16 22:23 temp
user@comp:~$ ls temp
user@comp:~$ cd temp
user@comp:~/temp$

```

I didn't have to use root access to change the permissions (and access the folder contents).

---

### Post by Bodsda on 2009-06-17
> **bigboy_pdb said:**
> That's exactly what I was talking about in my first post.

**This method does not work**:
```

sudo chmod a-rwx folder

```
(regardless of how you use chmod to change the file permissions)

Putting sudo in the front of chmod does not keep the owner of the folder from being able to view the contents. For someone else to view the contents he/she just has to run:
```

chomod u+rwx folder

```
(this can also be done in the "Permissions" tab under the file's "Properties")

In other words, **you can only hide a file/folder that is owned by you from other users who are using your account by changing the ownership of the file/folder.** Technically, since you no longer own the file/folder, it really isn't possible without encryption.

When I said that the method which was first posted doesn't work, this is what I was referring to.

This is a complete counter example:
```

user@comp:~$ mkdir temp
user@comp:~$ ls -ld temp
drwxr-xr-x 2 user user 4096 2009-06-16 22:20 temp
user@comp:~$ sudo chmod a-rwx temp
user@comp:~$ ls -ld temp
d--------- 2 user user 4096 2009-06-16 22:20 temp
user@comp:~$ cd temp
bash: cd: temp: Permission denied
user@comp:~$ ls temp
ls: cannot open directory temp: Permission denied
user@comp:~$ chmod u+rwx temp
user@comp:~$ ls -ld temp
drwx------ 2 dave dave 4096 2009-06-16 22:23 temp
user@comp:~$ ls temp
user@comp:~$ cd temp
user@comp:~/temp$

```

I didn't have to use root access to change the permissions (and access the folder contents).

Thats because you own the folder, but that method requires no password at all so doesnt fit the bill either... 

And whats wrong with running as root? Its not forbidden, I dont see why everyone is trying to over complicate the situation to which there is already an answer just because you dislike running an application as root.

---

### Post by macvr on 2009-06-17
> **bigboy_pdb said:**
> 
Putting sudo in the front of chmod does not keep the owner of the folder from being able to view the contents. For someone else to view the contents he/she just has to run:
```

chomod u+rwx folder

```
(this can also be done in the "Permissions" tab under the file's "Properties")
I'm not saying it is fool proof. and i do know the draw backs, but i dont know any other solution to this!

For such access the guest user has to go out of the way to access the folder and its content. 
My intentions are just to prevent access to friends/family who want to check out the system and prevent the accidental dropping into the folder and checking out the files...

And several times i kept forgetting to change the permissions back to a no read  state, hence i wanted the rechange of permissions to be automated. hence the executable file.

And the use of the gksudo in the .protector file was , if i didnt do it, any one can open the folder by just running the file! using gksudo prevents accidental access from the .protector file.


> **geo909 said:**
> congrats, this is a very nice and clever idea! 
Thank you.
> **geo909 said:**
> Also what you need is not really common. You are actually trying to lock folders and hide them from "yourself" (= your account).
I'd have to disagree that my situation is not common...

There are several programs available for windows users, to allow simple folder locking[i also do know that there are more complex programs which offer encryption].
But since i didnt find any thing that was a simple read prevention, i thought of this way.

My only problem with encryption/decyrption is the creation of the duplicate files and i'd have to delete the files.

I really hope someone comes up with a simple way to lock the folders. :)

---

### Post by bigboy_pdb on 2009-06-17
> **Bodsda said:**
> Thats because you own the folder

That was part of the assumption in the first post. The idea was to protect *your* files. What further supports this is that people responded as though having a different file owner is a different solution.

> **Bodsda said:**
> And whats wrong with running as root?

Nothing when it's required, done properly, and only used where it is absolutely necessary, but that's not the case here. One problem would be [privilege escalation]("http://en.wikipedia.org/wiki/Privilege_escalation").

When you type everything on the command line yourself, there isn't a problem with using sudo commands, but once you put them in a file that you own, someone can place a trojan sudo program in front and fake a failed login attempt while recording your root password.

If you have to ask what's wrong with running processes/applications as root then you need to do more research on Linux security.

---

### Post by macvr on 2009-06-17
> **bigboy_pdb said:**
> That was part of the assumption in the first post. The idea was to protect *your* files. What further supports this is that people responded as though having a different file owner is a different solution.

You are forgetting one aspect...  partitions ,
 and the partitions are used by several others too, so having a private folder on the separate partition might be owned by several users.

---

### Post by bigboy_pdb on 2009-06-17
> **macvr said:**
> You are forgetting one aspect...  partitions ,
 and the partitions are used by several others too, so having a private folder on the separate partition might be owned by several users.

I'm sorry. When I referred to owners, I meant to say groups or owners.

Although, regardless of that the rest of my point still stands.

**EDIT**: As a side note, for complicated group/ownership privilege arrangements you can use [ACLs]("http://en.wikipedia.org/wiki/Access_control_list").

---

### Post by numbness05 on 2009-06-18
Forgive me for I am probably making a huge error here but I tried this method of adding a password my desired folder which I too named "protector" just to save complications and this is what I get... could some one tell me where I have gone wrong along the way please
I have tried several times following these instructions but seem to hit this barrier every time 

daniel@daniel-desktop:~$  sudo chmod a-r /home/daniel/Public
daniel@daniel-desktop:~$ $touch .PROTECTOR
bash: .PROTECTOR: command not found
daniel@daniel-desktop:~$ $touch .PROTECTOR

Many thanks in advance
Kind regards

---

### Post by Jose Catre-Vandis on 2009-08-06
Was intrigued by this, as as the OP says, there are lots of ways to do this under Windows, but encryption seems the most sensible route in Ubuntu.

However, had a little play with this today, and came up with a bash script that provides a solution, of sorts, that should meet the OP's criteria, and be open to developing on to better things.

All previous posts from everyone saying this is not the way acknowledged and understood, my effort was as much about learning "what" could be done and how to do it.

Many thanks must go to ubuntuforums user cisco311, who gave me a great deal of help with how to find and use the user password hashes. So anyway, here we go:
> #!/bin/bash

#secret.sh

#Requirements:
# Zenity
# mkpasswd (?)
# python

#a script to open up a private folder, where permissions are
#set to "None", giving the logged in user and original owner of the folder
#read / write access.

#this works (under xubuntu and with thunar) when there are no other thunar
#windows open. Otherwise the permissions will be reset again - annoying.
#Would be good to know how to resolve this.

#this can work with any chosen password, it doesn't have to be a user,
#but the folder must be owned by the user.
#Use the command in the TESTPASS variable to generate hash strings, and
#youcan make up your own salt string

#please use your own hash string and salt string as these are examples only,
#for testing, the password is "blob" (no quotes), but may not give the same
#results on your machine? 

#echoing of variables have been commented out, but uncomment them if you need to debug/test

########################################################################

#USER VARIABLES
#hash copied from /etc/shadow for "chosen user"
USERFILE='$6$b.tYU/QzSx$j1SJXFQ7SCs6dG7vD4jCJ29X6Fi.OHPol7HJrIm4sNgKTCMkIrvh0DziPhjczryuJtrZMooK9W0/d1sxzXRio.'
#"the salt" - as you will see this is the set of characters between the second and third $ in the above string
USERSALT='b.tYU/QzSx'
#secret folder that the logged in user owns, change accordingly, use a ./hidden file for additional secrecy
SECRET='/home/user/.SecretFiles'
#file manager choice, e.g nautilus, thunar, pcmanfm, mc. If you install a second file manager,
#you can use this instead of your normal one to access the secret folder
FM=your/preferred/filemanager

#SCRIPT

#suggests closing all other file manager windows before running the script
zenity --info --title="Secret Folder Script" --text="You May Need To Close All Other File Manager Windows Before Proceeding"

#pops up a zenity dialog asking for your chosen users password
PASS=`zenity --entry --title="Secret Folder" --text="Enter your _password:" --entry-text "password" --hide-text`

#converts the plain text password given in the dialog to a sha-512 encrypted hash
TESTPASS=$(python -c "import crypt, getpass, pwd; print crypt.crypt('$PASS', '\$6\$"$USERSALT"\$')")

#echo "file manager $FM"
#echo "folder $SECRET"
#echo "pass $PASS"
#echo "salt $USERSALT"
#echo "hash $USERFILE"
#echo "testpass $TESTPASS"

#do the two hashes match?
if [ ! "$USERFILE" = "$TESTPASS" ]

then
#if they don't match, pop up a dialog to say you don 't have access
zenity --info --title="Secret Folder" --text="Sorry, No Access To Secret Folder"

else
#if they do match, give read / write permissions to your folder and ... 
chmod -R 700 "$SECRET"
#open up the folder - change fm to thunar or nautilus or pcmanfm if that's what you use
"$FM" "$SECRET"

#when the fm window is closed, resets the permissions to "None"
#allow some sleep time to let thunar shut down
#echo "sleeping"
sleep 5
#echo "File Manager Closed"
#reset permissions
chmod -R 100 "$SECRET" 2>dev>null
#echo "Permissions Reset"

fi

########################################################################

Even so, **cryptkeeper**, in the repos, offers much the same functionality, with encryption, and no need for sudo, with handy access from your icon tray

---

### Post by tenfishsticks on 2010-01-05
Wow, great work!  I've seen a lot of older posts looking something just like this.  I'm not that experienced with bash scripts, so I have a few minor questions about how to tailor this script.  I've changed the "\$6$" on line 51 to "\$1$" to get the hash value closer to the testpass value.   Here's my echo output.  What am I doing wrong here?

> file manager /usr/bin/nautilus
folder /etc/.dansguardian
pass blob
salt 4zWcNB0W
hash $1$4zWcNB0W$RHYFzUHEhk/pKQEL/kVjq/
testpass $1$4zWcNB0W$oU45aHkIwoQvzS7vqwBCI0


Where do I set the folder password, i.e. "blob"?  Is that just my user password?

---

### Post by Jose Catre-Vandis on 2010-01-21
Do you own /etc/.dansguardian with full permissions?

Refer to [this thread]("http://ubuntuforums.org/showthread.php?t=1232715&highlight=password&page=2") for more background info:

---

### Post by tenfishsticks on 2010-01-21
Excellent!  I looked at this website as well:
[http://www.pabloendres.com/tag/mkpasswd/]("http://www.pabloendres.com/tag/mkpasswd/")

My password encryption differs from the other users on the system, so I had to find which algorithm flag to pass to crypt.  In my example, $1$ is md5 whereas $6$ is sha-512.  Once I changed that, the script ran like a charm!  Thanks for your help!

---

