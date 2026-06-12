---
title: "Permission denied when running bash script"
date: 2015-01-09
forum: New to Ubuntu
---

### Post by gregory10 on 2015-01-09
I am making a .sh script. the commands in it work fine by themselves but now am trying to get it all working together as a .sh script
this initial script has only one of the functions I want to use. the one containing the command to open firefox with some webpages
gregory@gregory-Satellite-L500:~$ ~/Documents/bashtutes/bashtutes.sh             
bash: /home/gregory/Documents/bashtutes/bashtutes.sh: Permission denied
gregory@gregory-Satellite-L500:~$


The problem faced here is all about the script. this script is only one function with one command of the 3 I need to get working.
This script opens all files and associated apps with files in them. The commands all work fine in Konsole as manually executed commands.
That is they work fine as commands: but the problem I now face is getting them to work as part of a script in a .sh file.

the open kate in a session: konsole --new-tab -e kate -s bashtutes 
# executes  and opens a predefined session in kate perfectly, Happy about this finally found out how to do it so try it with the other apps

konsole --new-tab -e okular ~/Documents/bashtutes/w_mach02.pdf
# waaahooo yes finally it works got it right yes yes yes it was worth all that research

konsole --new-tab -e firefox [http://google.com/](http://google.com/) [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)
# yes successs waaahooooo can get any amount of site pages up in firefox for researching info on this project nice...

I would also like to know how to open yet another tab with one of the pre-set profiles I created in console settings but am happy to be able to 
have these 3 commands working. I can use the original default tab that is opened to execute these commands.

NEXT STEP
I need to put these in a script and aiming for:
gregory@gregory-Satellite-L500:~$ ~/Documents/bashtutes/bashtutes.sh 

the system seems to throw some sort of exception although it is only a function with a simple command that already works fine without extra privileges
Well I'm now at a stand still and need to make some progress can any shed some light on why or what to do?

This is the script. I am trying to get one function going at a time then put them all together in the one script.
the aim is to be able to open all files of one project with the one simple command in konsole.
I guess its like a little program in it's own right but simple yet effective. I need to get started using it and make some progress on my projects.

this is the first try at a script:
```

#!/bin/bash


function openffox () {
# webinfo4="firefox http://google.com/ https://wiki.ubuntu.com/CustomXSession" # this definitely works just as a command and not in this variable
    konsole --new-tab -e firefox http://google.com/ https://wiki.ubuntu.com/CustomXSession 
    return $?
#
echo "the internet connection is now opened all url's declared (the request message is sent to web services) firefox is set"
#
}


wtime=60
#
remotehost=google.com
function trigger {
  ping -qc 3 "$remotehost" >/dev/null    # >/dev/null outputs the ping to gooble.com '>' means output what is before the '>' to what is after the '>'
  return $?                              # here $? the outcome is returned: a ping will or won't happen because it has to pong or not pong
}


if [! trigger]; then  # from bash -c help =====>   [! expression]  True if expression is false.
echo
echo "internet connection is closed; check to see if you are connected to a network or the modem is plugged in: try opening the connection manually"
echo
echo "Your internet connection is closed and you cannot have your internet session unless you connect to the internet; no internet: firefox is closed"
echo
else
echo
echo "Internet connection good to go, opening instance of firefox"
echo
openffox;
echo
echo "firefox running, browser set to go: your webpages are ready, you can do your research"
fi

```

this is what I get when trying to execute it in konsole:
gregory@gregory-Satellite-L500:~$ ~/Documents/bashtutes/bashtutes.sh             
bash: /home/gregory/Documents/bashtutes/bashtutes.sh: Permission denied
gregory@gregory-Satellite-L500:~$

Permission denied? what does that mean? 
don't know where to start on this but happy with progress so far. Below is a print-screen just taken after executing the commands manually
It's the result I'm looking for only using a script and not by executing 3 separate commands one by one.



[ATTACH=CONFIG]259133[/ATTACH]

It's not so easy to see from this thumbnail but there are now three tabs open and still got the original tab to work in so it is adequate if I can
just get those three commands working in a script. the reason I put so much into explaining this is that I know these commands could help a lot of people.
having a script to do all this would be a real asset to anyone wanting to be well organised. I hope this helps anyone that is interested.
Am hoping some will want to get involved with finishing this script and getting it working for that reason. It's taken me a while to get to this stage.
the konsole commands differ slightly with any other terminal like gnome and others. 


Just have to get past this hurdle and I'm most of the way there.
gregory@gregory-Satellite-L500:~$ ~/Documents/bashtutes/bashtutes.sh             
bash: /home/gregory/Documents/bashtutes/bashtutes.sh: Permission denied
gregory@gregory-Satellite-L500:~$

thanks so much for any help you can give. I really do appreciate it and have had success with other problems I have asked about here in this forum
thanks again all the best for the year ahead
G

---

### Post by sandyd on 2015-01-09
Linux's file permissions system mainly consists of 3 parts

[LIST]
[*]read/write/execute privileges
[*]user/group ownership
[*]acls
[/LIST]

The one you are facing is read/write/execute Privileges

**Read/Write/Execute Privileges**
Each file and folder has three sets of read/write/execute privileges.
They are...
[LIST]
[*]user
[*]group
[*]other
[/LIST]
The ls command allows you to list the contents of a directory, or check if a file exists.
When you do a ls -l on a directory, for example (in this case, the tilde represents your home folder)
```

ls -l ~
```

You will get output similar to
```

drwxr-xr-x 1 dash-owner dash-group        0 Dec 22 11:36 Music
drwxrwxr-x 1 dash-owner dash-group      374 Jan  3 15:53 openvpn
drwxrwxr-x 1 dash-owner dash-group      236 Dec 31 13:30 ownCloud
drwxr-xr-x 1 dash-owner dash-group     1760 Jan  3 12:54 Pictures
drwxr-xr-x 1 dash-owner dash-group        0 Dec 22 11:36 Public
-rw-rw-r-- 1  dash-owner dash-group     3602 Jan  6 18:56 index.html

```

In the first column, the first character (for files and directories at least for simplicity) indicates if the object is a file (-) or directory (d).
The next three characters represent the read/write/execute privileges for the owner, which in this case is dash-owner. The three characters after that represent read-write privileges for the group (dash-group), and the last three characters in the column represent privileges for 'other' users.

The characters:
[LIST]
[*]r = read
[*]w = write
[*]x = execute
[*]- = no privilege for the character that should be there
[/LIST]
In order to read a file, a user must have read (r) privileges to a file. In order to write to a file, a user must have write (w) privileges to a file. In order to execute a file, a user must have execute (x) privileges to a file.

In the above example, you can see that dash-owner has no privileges to execute index.html. By default, files are created with no execute privileges.

You can change the permissions for a file by using a utility called chmod.

To use chmod, you can calculate the permissions value that you want to set the file to.
This can be done by adding the values below for each set of permissions (user/group/other).
[LIST]
[*]r = 4
[*]w = 2
[*]x = 1
[/LIST]



For example, to set permissions to allow only the owner to read, but not write or execute the file, you would use
user=4+0+0
group=0+0+0
other=0+0+0
```
chmod 400 /path/to/file
```

To allow only the owner and group to execute, write, and read a file, you would use
user=4+2+1
group=4+2+1
other=0
```
chmod 770 /path/to/file
```

To allow the owner and group to execute, write, and read a file, while allowing other users to execute it, you would use
user=4+2+1
group=4+2+1
other=4+0+1
```
chmod 775 /path/to/file
```

You can also modify a file/directory's privileges using chmod.

Using the following characters,
[LIST]
[*]u = user
[*]g = group
[*]o = other
[/LIST] you can add (+) or subtract(-) privileges from files and directories by using the following command format.
```

chmod (u/g/o)(+/-)(privilege) /path/to/file
```

For example, to add an execute privilege for other users,
```

chmod o+x /path/to/file
```



**Side note**:
For directories, the (x) privilege does not mean execute. Instead, it is the pass-through privilege, a setting that allows users to enter (pass-through) a directory. When not set for a user/group/other, the particular user/group/other is not allowed to enter the directory

**Side note 2**:
It is _not_ a good idea to give files and directories all a chmod of 777 for simplicity. This undermines Linux's security system and breaks programs that require secure privileges be set before running (ex: ssh)

**Side Note 3**
If you don't like using a terminal, you can right click the script, and go to the permissions tab where you can select the checkbox named 'Allow executing file as program'

Hope that helps!

---

### Post by gregory10 on 2015-01-10
@sandyd
thank you again, I went for the easy option right clicked and went to properities -> permissions tab. ticked the Ls execute box and it works but will re-read all you wrote in here. 
Solved first time thanks for Sandyd and the forum.
that has to be the first time I wrote a script and it worked as is first time just as I planned it.
Really chuffed about this.
thanks for all

---

### Post by nerdtron on 2015-01-10
> **gregory10 said:**
> @sandyd
thank you again, I went for the easy option right clicked and went to properities -> permissions tab. ticked the Ls execute box and it works but will re-read all you wrote in here. 
Solved first time thanks for Sandyd and the forum.
that has to be the first time I wrote a script and it worked as is first time just as I planned it.
Really chuffed about this.
thanks for all

Just a side note, even if the script is not executable you can explicitly tell the terminal to run it.

For example if you script is made for bash, you can run:
```
bash ~/path/to/myscript.sh
```

or if your script is made in perl,
```
perl ~/path/to/perl/script.pl
```

---

### Post by gregory10 on 2015-01-10
I want to mark this as solved but there is one part of this puzzle that I have not got solved yet
There is one thing: [IMG]Gregory/Home/Documents/bashtutes/tabsnapshot.png[/IMG]

I have been researching this did a lot of searches on google
but haven't been able to find the command or a command that makes it happen
I need to include in the script I am making and function that opens a pre-set profile setting in bash
I have three stored in settings and would like to open any one of them.

does anybody know a command that will do this?
it seems to go to a default terminal each time I try...

```

Warning: Could not find 'bash-tutes', starting '/bin/bash' instead.  Please check your profile settings.


gregory@gregory-Satellite-L500:~$ 

```
another tab does open but it has this message in it
I guess there is a file somewhere that needs the profile setting in it
thanks for you help
G

PS 
tried to include a snapshot image showing the way a tab is opened manually on screen but it doesn't seem to appear on the page
its on the konsole file menue: file->newtab->list is there
click on one of those profile set up in the list using setting profile manager and it will appear there in a new tab
I want to be able to have this happen as part of my script.
Can anybody tell me how to do this?
thanks again for you help.

---

### Post by steeldriver on 2015-01-10
I'm confused - are you talking about **bash** profiles or **gnome-terminal** profiles? exactly what command is resulting in the "Could not find 'bash-tutes'..." warning?

---

### Post by nerdtron on 2015-01-10
You can run your script with "bash -x /path/to/myscript.sh" so that we can see which line causes that error.

---

### Post by gregory10 on 2015-01-10
@ steeldriver
thats all fixed
thanks for asking
I use Konsole KDE Kubuntu
It was a permissions problem and followed sandyd's instructions: changed the permission using right click->properties->permissions->tickbox
the script works fine now. Using the script as is still got some refinements but it does what I need.

I am currently learning using some bash tutorials
I often use bash :~$ help
that's the best and simplest place to start because you get listed all the other ways to get help with bash scripts and info needed
and it happens right there in the terminal window.

---

### Post by gregory10 on 2015-01-10
@nerdtron
here is what you asked for

```
gregory@gregory-Satellite-L500:~$ bash -x ~/Documents/bashtutes/bashtutes.sh+ wtime=60
+ remotehost=google.com
+ '[!' 'trigger]'
/home/gregory/Documents/bashtutes/bashtutes.sh: line 20: [!: command not found
+ echo


+ echo 'Internet connection good to go, opening instance of firefox'
Internet connection good to go, opening instance of firefox
+ echo


+ openffox
+ konsole --new-tab -e firefox http://google.com/ https://wiki.ubuntu.com/CustomXSession
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
+ return 0
+ echo


+ echo 'firefox running, browser set to go: your webpages are ready, you can do your research'
firefox running, browser set to go: your webpages are ready, you can do your research
gregory@gregory-Satellite-L500:~$ 



```
thanks for your help still got things to refile on that script but iw works as far the main aim: the requested webpages are there to use.

The next (main) problem I'm facing is finding the how to of opening a new tab in bash with a re-set profile in it and be able to work with this bashtutes project
I have one setup called bash-tutes (I will try sending a thumbnail along with this as ilustration. the thumbnails seem a bit small but will try).
If I go to the graphic manue at the top of konsole settings is there and in that is profile manager and can setup a profile with ease.
Once the profile is setup with the colors for text and background and anything else then I can find it under file=> newtab->the list of profiles

[ATTACH=CONFIG]259162[/ATTACH]

The thumbnail above shows the menue I am talking about, I can get a tab with the bash-tutes profile manually: its at the top of the small flag list.
What I need is a command that causes that to happen. then I put the command in the script; along with the others and I got a nice little program that opens
all of the files and apps I need to do any tasks for the project: including one tab specially for the use of bash terminal in the KDE konsole.

Thanks again for your help
G

---

### Post by gregory10 on 2015-01-19
I'm going to have to put this as solved but not satisfied my question is fully answered because it is about the whole script not just the permissions issue.
To spite that the permissions issue was answered and quickly. thanks to all who helped.

I still need to know:
1. How to open a pre-set bash session in a new terminal as part of the script.
2. Part of the original test script is not working: it's the part that test's if the internet connection is open.

I tried many commands with both but nothing works so far. though I am sure there are simple ways to do it
just like the ones I have tried so far.
```

+ remotehost=google.com
+ '[!' 'trigger]'
/home/gregory/Documents/bashtutes/bashtutes.sh: line 20: [!: command not found
+ echo
```
So the function trigger is not working and trigger is this function below:
```

wtime=60
#
remotehost=google.com
function trigger {
  ping -qc 3 "$remotehost" >/dev/null   
  return $?                              
}
```
I need someone to tell me what is wrong with this function please
the '!' is supposed to work but bash seems to be saying there is no such command but it's there in the manual 
It should be that it results true if the term it's used in is false. In this case if google is pinged and there is ping return from google site then it's false
and if there is not then it is true. Maybe I have it wrong but I don't think so.

For the other I get the impression that something needs to be stored in an apropriate file
.profile or .profilerc
I think they are the files that need editing but where are they how do find them
I tried a lot of things.

I need to know how to edit those files and also the command to use to open the new tab once the profile is there to be opened using a command in the terminal
and also I need a function that test pings google to check if the internet connection is running: one that will  --->> if 'yes' then 'blah' else 'blah'. <<---

---

### Post by Holger_Gehrke on 2015-01-19
'[' is a short name for the test command. '[!' is an unknown command. You're missing a space between '[' and '!'. Also test can't execute functions. It just does tests. Leave out the '[' and the ']' . You're just checking the return status of the function, and if already does that. A '!' before a command (or a function call) inverts the return value -- zero (everything is ok) becomes one, non-zero (something is wrong) becomes zero, so it should be 'if ! trigger ; then ...' or you could leave out the '!' and switch the 'then ' and 'else ' actions around.

You might want to read the manual page for the bash. 'man bash'

---

### Post by gregory10 on 2015-01-19
@ Holger_Gehrke
Thank you very much
I eliminated those '[' ']' brackets and it works fine without them also tried it without '>/dev/null' to be able to read the success of the packets recieved back
It's all good now. thanks such a simple thing that spacing so thank you for making me aware of it.
It's really good to have that part of my question resolved as well as the main part. Helps me a lot.

I'm not entirely new to scripting and making functions but bash and konsole are entirely new to me at this time
Thank you for you help with this question its a big step forward to have this function work so well.

---

### Post by Holger_Gehrke on 2015-01-19
And two more small hints:
1) Use parameters in your functions, not global variables. It makes re-use of functions easier. Instead of 'ping -qc3 $remotehost' use 'ping -qc3 $1' and call the function with 'trigger $remotehost'
2) You don't need to explicitly return $?. The exit status of the function is the exit status of the last executed command.

---

