---
title: "Bash scripting contests"
date: 2013-02-28
forum: Programming Talk
---

### Post by nwalkey on 2013-02-28
I wasn't sure where to put this, so please move it if it needs to be somewhere else.

When I started using blender, blenderartists.org had an awesome section of its forum where they hosted timed blender competitions. People would pick a topic or object and create the best thing they could in the given time period. It might be a day or two or it might be only 20 minutes. Afterward the community could vote on who's was the best. What I'm wondering is if there is anything like this for shell scripting. I think it would be cool if there were something like that but for bash scripting. It would be a great way for beginners to learn alot about bash as well as for more experienced individuals to just have some fun while scripting. There could even be some really useful/cool scripts that come out of it. I'd like to know if there's anyone else interested in doing this or if it already exists somewhere else??

---

### Post by lianne_john07 on 2013-03-01
+1 for this, coz i am bash scripter beginner.

---

### Post by beejee on 2013-03-01
Upvote, I'd love this too! 
I'm always on the lookout for new scripting techniques and tricks, this way we should gather a nice collection of example scripts.

---

### Post by slickymaster on 2013-03-01
The idea sounds great. Maybe something like [Beginners Team Programming Challenges Index]("http://ubuntuforums.org/showthread.php?t=1714324") and [Advanced programming exercises]("http://ubuntuforums.org/showthread.php?t=1750795").

---

### Post by nwalkey on 2013-03-01
Sweet, well sounds like we have enough interest to get it started. I'm sure more people will jump on board later. It would be awesome if it got popular enough to have its own subsection of the forum. I think we can either have one thread for the whole thing(very hard to vote) or we can create new threads for each new contest.

Weekly+ or daily would be the best so that there is still a time crunch to it but so that we don't have to set up IRC channels or anything to moderate the time limit other than when the person posted their submissions.

Some rules:
1) no malicous code (rm /* or others that can wreck a system)
2) explain things with comments, we're all learning and this helps when reading the script (should lose credit toward winning without this)
3) no exterior programming languages (perl, python, etc., I think sed and awk are okay though)
4) if you use programs that are not typically installed by default, let it be known in the script and when you post
5) have some fun, be creative, and judge on creativity as well as function
Anyone else think of some rules let it be known.

Lets do it!

I'll start off the contest with a fairly easy one: the challenge is to duplicate all files of a users home folder to a new users home folder, then remove all the config files and documents, and leave the old user's home folder as it were created from a fresh installation. I'll give everyone 3 days to complete and upload their scripts.

---

### Post by ugm6hr on 2013-03-01
Moved: not a support request.
(Good luck with this endeavour)

---

### Post by Malsasa on 2013-03-01
Where is the LIKE button? I agree with this idea :) 

A contest like Google Summer of Code :D maybe...

---

### Post by nwalkey on 2013-03-03
Here's my script. Wanted to make it good. Got some great practice with various loops and functions as well as putting in failsafes and making it a bit interactive :)

```
#!/bin/bash 

#variables to be used...

newuser=              #variable used to create a new user
currentuser=$HOME     #current user variable, reads $HOME variable
yesno=                #variable for yes/no answers
rootid=0          #vairable to determine root status
newexist=          #used to determine if we are using a new or existing user

#newuser function
newuser()
{
echo "what would you like the new user's name to be"
read newuser
echo "the new user will be $newuser"
echo "creating new user..."
adduser $newuser
}


#function to ask if the user is new or old
newold()
{
echo "Are you creating a new user or moving files to an existing account"
echo '[new/existing]'
read newexist
if [ "$newexist" = "new" ]; then
newuser
else
echo "what is the name of the account you wish to move files to"
read newuser
fi
}

#this function copies all the user's files over
moveuser()
{
echo "the current user is $currentuser"
echo "do you wish to move this user to /home/$newuser ?"
echo "y/n"
read yesno                             #asks for user input
if [ "$yesno" = "n" ] || [ "$yesno" != "y" ]                #if the answer is n or not y then ask for new user name
then
   echo "enter the username of the account to be moved"  
   read currentuser                    #gets user input and puts into currentuser variable
   echo "$currentuser"
   currentuser=/home/$currentuser            #if $currentuser is left as just an inputed name "user" then it will try to use user instead of /home/user so set variable to use /home/$currentuser
   echo "$currentuser"
   echo "this is the right user?"
   echo "[y/n]"
   read yesno
   if [ "$yesno" != "y" ]; then                #this if statement is needed to prevent wrong inputs, eg no instead of n
      echo "you have not entered a valid answer"
      echo "exiting status 1"
      exit 1
   fi
fi
                            #when the user is set right it now moves all the files over to the new user
mv "-f" $currentuser/* /home/$newuser        #moves files recursively and forcefully, probably need if we use the adduser method
echo "files have been moved from $currentuser to $newuser"
echo "removing old files"
rm -Rf $currentuser/*
cd $currentuser                    #moves to the old user's folder
echo "making new directories"
mkdir Desktop Documents Downloads Music Pictures Videos  #makes all the default user directories for ubuntu
echo "changing user permissions"
chown $newuser /home/$newuser/*            #changes file ownership, otherwise everything is owned by root
chmod 755 /home/$newuser/*            #changes file permissions, rwx,r-x,r-x, read,write, execute for user and read execute for else
}


#the script
#start off testing for root, because this cannot be done without it and should exit if you are not root

if [ "$UID" -eq "$rootid" ]                #checks for root
then
   newold                        #calls newuser function
   moveuser                        #calls move user function
else                            #If you are not root then it exits
   echo "You are not root. Run the script again with sudo"
   echo "exiting now"
   exit 0
fi

exit 0
```

---

### Post by ofnuts on 2013-03-03
```

mv "-f" $currentuser/* /home/$newuser  #moves files recursively and forcefully, probably need if we use the adduser method 
echo "files have been moved from $currentuser to $newuser" 
echo "removing old files" 
rm -Rf $currentuser/* 

```

[LIST]
[*]Your  "mv" overlooks all the files/directories with a leading dot ("*" doesn't list them, ".*" does...)
[*]Then you attempt to erase what? What files do you expect to see in $currentuser since you have moved them elsewhere?
[*]Fortunately this doesn't erase the overlooked "dot files" for the very same reason
[*]Why all that complexity when you can just rename $currentuser to $newuser?
[/LIST]

---

### Post by nwalkey on 2013-03-04
lol good call on that. I think I missed the mark on that one. I was experimenting with too many things that I'm just learning and I think I've over looked one of the more important aspects of scripting in doing so: keep it simple. Thanks for pointing that out though.

---

### Post by ofnuts on 2013-03-04
Two other aspects are also "keep it readable", and "minimize the WTF factor" :)

And before starting contests the participants have to answer two questions:


[LIST]
[*]what are the criteria for "best"?
[*]who are the judges?
[/LIST]
 
Audience voting isn't the solution, at least not if you want to select good stuff (as demonstrated by very many TV shows :)).

---

### Post by conradin on 2013-03-05
Aw man, This is a great idea, I wish it had its own section in the dev forums! 
Also: Im going to be waiting for the second challenge. 

there could be panel judges, and participants could also vote if there was a poll.

---

### Post by XQbABnY on 2013-10-23
What happened to this thread/idea!!! I just ran into it and I'm hoping it continued somewhere?? Anyone know anything? I would love to build some muscle by competing - not that I am much good yet, but it's such a cool way to learn from each other!

---

### Post by nwalkey on 2013-10-24
XQbABnY, It would be cool to revive the idea. I don't have much time to play around with scripting but I think there are a ton of people that could benefit and we could make some pretty cool/useful scripts in the process. If anyone wants to start up again that would be cool. Just post an idea for a script and start it up again!

---

