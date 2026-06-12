---
title: "BASh Script Permission Denied"
date: 2011-06-10
forum: Programming Talk
---

### Post by GrantStoner on 2011-06-10
I'm working on a personal script to install a complete arsenal of pentest tools. Yes, I know, it's very incomplete. I just got on Ubuntu last night. Here is the script I'm running (as a regular, non-privileged user):```
#! /bin/bash

initializeANSI()
{
  esc=""

  blackf="${esc}[30m";   redf="${esc}[31m";    greenf="${esc}[32m"
  yellowf="${esc}[33m"   bluef="${esc}[34m";   purplef="${esc}[35m"
  cyanf="${esc}[36m";    whitef="${esc}[37m"
  
  blackb="${esc}[40m";   redb="${esc}[41m";    greenb="${esc}[42m"
  yellowb="${esc}[43m"   blueb="${esc}[44m";   purpleb="${esc}[45m"
  cyanb="${esc}[46m";    whiteb="${esc}[47m"

  boldon="${esc}[1m";    boldoff="${esc}[22m"
  italicson="${esc}[3m"; italicsoff="${esc}[23m"
  ulon="${esc}[4m";      uloff="${esc}[24m"
  invon="${esc}[7m";     invoff="${esc}[27m"

  reset="${esc}[0m"
}

clear

if [ "$UID" != "0" ]; then
    printf "\nRe-running as root... "; tput sgr0
    exec su -c $0
fi

initializeANSI
cat << EOF
${greenf}                       ,
                      dM
                      MMr
                     4MMML                  .
                     MMMMM.                xf
     .              "M6MMM               .MM-
      Mh..          +MM5MMM            .MMMM
      .MMM.         .MMMMML.          MMMMMh
${yellowf}       )MMMh.        MM5MMM         MMMMMMM
        3MMMMx.     'MMM3MMf      xnMMMMMM"
        '*MMMMM      MMMMMM.     nMMMMMMP"
          *MMMMMx    "MMM5M\    .MMMMMMM=
           *MMMMMh   "MMMMM"   JMMMMMMP
             MMMMMM   GMMMM.  dMMMMMM            .
              MMMMMM  "MMMM  .MMMMM(        .nnMP"
   ..          *MMMMx  MMM"  dMMMM"    .nnMMMMM*
${redf}    "MMn...     'MMMMr 'MM   MMM"   .nMMMMMMM*"
     "4MMMMnn..   *MMM  MM  MMP"  .dMMMMMMM""
       ^MMMMMMMMx.  *ML "M .M*  .MMMMMM**"
          *PMMMMMMhn. *x > M  .MMMM**""
             ""**MMMMhx/.h/ .=*"
                      .3P"%....
                    nP"     "*MMnx    ${reset}
EOF
printf "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
printf "\nI'm gonna be doing a lot of ****, SO JUST BE PATIENT.\n"
printf "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n"
sleep 1
printf "Autoremoving orphaned deps...\n\n"
sleep 1
apt-get autoremove >/dev/null || exit 1
printf "Autocleaning old repos...\n\n"
sleep 1
apt-get autoclean > /dev/null || exit 1
printf "Cleaning ALL repos...\n\n"
sleep 1
apt-get clean > /dev/null || exit 1
printf "Updating repos...\n\n"
sleep 1
#apt-get update > /dev/null || exit 1

printf "...SUCCESS!...\n\n"
sleep 1

printf "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n"
read -p "Now you've got some options!
1) Grab and install Metasploit?
2) Grab and install S.E.T.?
3) Grab and install Aircrack-ng?

(Enter a # to continue with it): " -n1 variable
case $variable in
    1)
        wget http://updates.metasploit.com/data/releases/framework-3.7.1-linux-full.run
        ./framework*
        rm -rf framework*        
    ;;
    2)
        printf "\n\nYou pressed 2!\n\n"
    ;;
    3)
        printf "\n\nYou pressed 3!\n\n"
    ;;
    *)
        printf "\n\nAny other key will exit to main menu when I figure it out.\n\n"
    ;;
esac
sleep 1

printf "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n"

exit 0

```I've made it such that script should ask you to log in as root, then it runs again. So you can run it as root or regular user. However, once it gets to "./framework*" I get the following output:```
Re-running as root... Password: 

                       ,
                      dM
                      MMr
                     4MMML                  .
                     MMMMM.                xf
     .              "M6MMM               .MM-
      Mh..          +MM5MMM            .MMMM
      .MMM.         .MMMMML.          MMMMMh
       )MMMh.        MM5MMM         MMMMMMM
        3MMMMx.     'MMM3MMf      xnMMMMMM"
        '*MMMMM      MMMMMM.     nMMMMMMP"
          *MMMMMx    "MMM5M\    .MMMMMMM=
           *MMMMMh   "MMMMM"   JMMMMMMP
             MMMMMM   GMMMM.  dMMMMMM            .
              MMMMMM  "MMMM  .MMMMM(        .nnMP"
   ..          *MMMMx  MMM"  dMMMM"    .nnMMMMM*
    "MMn...     'MMMMr 'MM   MMM"   .nMMMMMMM*"
     "4MMMMnn..   *MMM  MM  MMP"  .dMMMMMMM""
       ^MMMMMMMMx.  *ML "M .M*  .MMMMMM**"
          *PMMMMMMhn. *x > M  .MMMM**""
             ""**MMMMhx/.h/ .=*"
                      .3P"%....
                    nP"     "*MMnx    
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I'm gonna be doing a lot of ****, SO JUST BE PATIENT.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Autoremoving orphaned deps...

Autocleaning old repos...

Cleaning ALL repos...

Updating repos...

...SUCCESS!...

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Now you've got some options!
1) Grab and install Metasploit?
2) Grab and install S.E.T.?
3) Grab and install Aircrack-ng?

(Enter a # to continue with it): 1--2011-06-10 11:58:24--  http://updates.metasploit.com/data/releases/framework-3.7.1-linux-full.run
Resolving updates.metasploit.com... 184.154.104.2
Connecting to updates.metasploit.com|184.154.104.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 162755674 (155M) [application/octet-stream]
Saving to: `framework-3.7.1-linux-full.run'

100%[======================================>] 162,755,674  686K/s   in 4m 0s   

2011-06-10 12:02:24 (663 KB/s) - `framework-3.7.1-linux-full.run' saved [162755674/162755674]

BASh/./script0.sh: line 86: ./framework-3.7.1-linux-full.run: Permission denied
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

grant@L1NUX ~ $ 
```Does it have anything to do with Ubuntu using "sudo"? Or does it actually run as root, with "su"? I remember using that same snippet for metasploit for a Fedora script I wrote, and it worked just fine as non-priv user. Asked for the passwd, re-ran as root, and all was fine. Why isn't it working now?

---

### Post by papibe on 2011-06-10
I haven't take a detail look at your script but my impression is that the downloaded file it is saved as a regular file, thus it doesn't have execution permission assigned. That can be solve by adding the permission before run it, or by making a call like "bash yourfile.run"

Hope it helps.

BTW: Nice ASCII art!

---

### Post by Arndt on 2011-06-10
> **GrantStoner said:**
> Does it have anything to do with Ubuntu using "sudo"? Or does it actually run as root, with "su"? I remember using that same snippet for metasploit for a Fedora script I wrote, and it worked just fine as non-priv user. Asked for the passwd, re-ran as root, and all was fine. Why isn't it working now?

My guess is that you need to set the execute bit on the script you fetched, sudo or not. Between wget and calling it, do

chmod +x framework*

---

### Post by GrantStoner on 2011-06-10
> **papibe said:**
> I haven't take a detail look at your script but my impression is that the downloaded file it is saved as a regular file, thus it doesn't have execution permission assigned. That can be solve by adding the permission before run it, or by making a call like "bash yourfile.run"

Hope it helps.

BTW: Nice ASCII art!
Thanks. :) Took some time to get it right and color it. Lol.
> **Arndt said:**
> My guess is that you need to set the execute bit on the script you fetched, sudo or not. Between wget and calling it, do

chmod +x framework*
Oh my gosh. I cannot believe I didn't check that. Thanks. I believe I even had the chmod command in there before I started to panic and rewriting it. >_<

Plus, I changed
```
[ "$UID" != "0" ]
```
to
```
[ $UID != 0 ]
```
Is this right? From what I understand, using the quotes would read it as a string and I'd need to use "-ne" instead of "!=" right? Getting rid of the quotes allows it to be read as an integer right?

---

### Post by hakermania on 2011-06-10
Yes, it's the executable bit, once you downoad the file you need the executable bit
EDIT:
between integer values you should better use -eq (equal) or -ne (not equal) (-lt less than) etc

---

### Post by GrantStoner on 2011-06-10
> **hakermania said:**
> Yes, it's the executable bit, once you downoad the file you need the executable bit
EDIT:
between integer values you should better use -eq (equal) or -ne (not equal) (-lt less than) etc
Isn't "-ne" for strings and "!=" for integers?

---

### Post by hakermania on 2011-06-10
> **GrantStoner said:**
> Isn't "-ne" for strings and "!=" for integers?

Yes, and for strings you had better use
```
if [[ $var1 = $var2  ]]; then
```
otherwise for security you need the X hack (don't care about it)

---

### Post by GrantStoner on 2011-06-10
Hmmm... Added the chmod part.
```
#! /bin/bash

initializeANSI()
{
  esc=""

  blackf="${esc}[30m";   redf="${esc}[31m";    greenf="${esc}[32m"
  yellowf="${esc}[33m"   bluef="${esc}[34m";   purplef="${esc}[35m"
  cyanf="${esc}[36m";    whitef="${esc}[37m"
  
  blackb="${esc}[40m";   redb="${esc}[41m";    greenb="${esc}[42m"
  yellowb="${esc}[43m"   blueb="${esc}[44m";   purpleb="${esc}[45m"
  cyanb="${esc}[46m";    whiteb="${esc}[47m"

  boldon="${esc}[1m";    boldoff="${esc}[22m"
  italicson="${esc}[3m"; italicsoff="${esc}[23m"
  ulon="${esc}[4m";      uloff="${esc}[24m"
  invon="${esc}[7m";     invoff="${esc}[27m"

  reset="${esc}[0m"
}

clear

if [ $UID != 0 ]; then
    printf "\nRe-running as root... "; tput sgr0
    exec su -c $0
fi

initializeANSI
cat << EOF
${greenf}                       ,
                      dM
                      MMr
                     4MMML                  .
                     MMMMM.                xf
     .              "M6MMM               .MM-
      Mh..          +MM5MMM            .MMMM
      .MMM.         .MMMMML.          MMMMMh
${yellowf}       )MMMh.        MM5MMM         MMMMMMM
        3MMMMx.     'MMM3MMf      xnMMMMMM"
        '*MMMMM      MMMMMM.     nMMMMMMP"
          *MMMMMx    "MMM5M\    .MMMMMMM=
           *MMMMMh   "MMMMM"   JMMMMMMP
             MMMMMM   GMMMM.  dMMMMMM            .
              MMMMMM  "MMMM  .MMMMM(        .nnMP"
   ..          *MMMMx  MMM"  dMMMM"    .nnMMMMM*
${redf}    "MMn...     'MMMMr 'MM   MMM"   .nMMMMMMM*"
     "4MMMMnn..   *MMM  MM  MMP"  .dMMMMMMM""
       ^MMMMMMMMx.  *ML "M .M*  .MMMMMM**"
          *PMMMMMMhn. *x > M  .MMMM**""
             ""**MMMMhx/.h/ .=*"
                      .3P"%....
                    nP"     "*MMnx    ${reset}
EOF
printf "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
printf "\nI'm gonna be doing a lot of ****, SO JUST BE PATIENT.\n"
printf "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n"
sleep 1
printf "Autoremoving orphaned deps...\n\n"
sleep 1
apt-get autoremove >/dev/null || exit 1
printf "Autocleaning old repos...\n\n"
sleep 1
apt-get autoclean > /dev/null || exit 1
printf "Cleaning ALL repos...\n\n"
sleep 1
apt-get clean > /dev/null || exit 1
printf "Updating repos...\n\n"
sleep 1
#apt-get update > /dev/null || exit 1

printf "...SUCCESS!...\n\n"
sleep 1

printf "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n"
read -p "Now you've got some options!
1) Grab and install Metasploit?
2) Grab and install S.E.T.?
3) Grab and install Aircrack-ng?

(Enter a # to continue with it): " -n1 variable
case $variable in
    1)
        wget http://updates.metasploit.com/data/releases/framework-3.7.1-linux-full.run
        chmod +x framework*
        ./framework*
        rm -rf framework*        
    ;;
    2)
        printf "\n\nYou pressed 2!\n\n"
    ;;
    3)
        printf "\n\nYou pressed 3!\n\n"
    ;;
    *)
        printf "\n\nAny other key will exit to main menu when I figure it out.\n\n"
    ;;
esac
sleep 1

printf "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n\n"

exit 0

```
And now I get that the file isn't even there. :(
```
100%[======================================>] 162,755,674  352K/s   in 4m 36s  

2011-06-10 12:49:25 (576 KB/s) - `framework-3.7.1-linux-full.run' saved [162755674/162755674]

BASh/./script0.sh: line 87: ./framework-3.7.1-linux-full.run: No such file or directory
```

---

### Post by hakermania on 2011-06-10
Weird I can say, I just tried with a file to my local server and seems to work fine, you could try instead of
./framework*
```
"$(pwd)"/framework*
```
and you could also try to put a 
sleep 1
between the wget and ./framework* command so as to ensure that the download has finished

---

### Post by GrantStoner on 2011-06-10
I will try that in a second. For now I commented out the "rm -rf" piece. And will do an "ls" when it's done if I get the same error. If it's there and it still can't find it, then your suggestion is surely next! I'm at my whit's-end. >_<

It's strange though that I only put "./framework*" and can autcomplete the name, but then say it's not there. How does it know the full name if it's not there?!

EDIT:
```
100%[======================================>] 162,755,674  466K/s   in 7m 50s  

2011-06-10 13:06:55 (338 KB/s) - `framework-3.7.1-linux-full.run' saved [162755674/162755674]

BASh/./script0.sh: line 87: ./framework-3.7.1-linux-full.run: No such file or directory
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

grant@L1NUX ~ $ ls
BASh       Downloads                       Pictures    Templates
Desktop    framework-3.7.1-linux-full.run  Public      Videos
Documents  Music                           script1.sh
grant@L1NUX ~ $
```

---

### Post by hakermania on 2011-06-10
On one hand, I cannot understand why you use wild-cards (*) supposing that you input the full filename into wget command, so, what's the point? 
On the other hand, using the whole path is more secure, because you could have executed any other framework* file if present

---

### Post by GrantStoner on 2011-06-10
True. I probably did this because at 2am in the dark I didn't want to find the "-.3" etc., keys. This script is faaar from finished. By the time it's done everything will likely be specified. At this stage, only one program.

---

### Post by GrantStoner on 2011-06-10
Oh yeah, I incorporated you other suggestions as well, and still got:
```
100%[======================================>] 162,755,674  636K/s   in 4m 39s  

2011-06-10 13:14:52 (570 KB/s) - `framework-3.7.1-linux-full.run' saved [162755674/162755674]

BASh/./script0.sh: line 88: /home/grant/framework-3.7.1-linux-full.run: No such file or directory
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

grant@L1NUX ~ $ ls
BASh       Downloads                       Pictures    Templates
Desktop    framework-3.7.1-linux-full.run  Public      Videos
Documents  Music                           script1.sh
grant@L1NUX ~ $ 
```

---

### Post by hakermania on 2011-06-10
Use the ab solute path, there is no reason not to do this, but if you've stack with this problem I'll try to figure it out. Be sure that both the script and the framework* file are at the current path in which you are in...

---

### Post by hakermania on 2011-06-10
I just tried your sript and works just fine at me, the metasploit framework installation opens normally
Linux MaD-pc 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by GrantStoner on 2011-06-11
> **hakermania said:**
> Use the ab solute path, there is no reason not to do this, but if you've stack with this problem I'll try to figure it out. Be sure that both the script and the framework* file are at the current path in which you are in...
I have tried this as well. You mean telling it directly where to look and do things such as "/path/to/metasploit-framework"? I got the same errors, that it wasn't there. And I used the full -3.7.1-linux-full.run name.
> **hakermania said:**
> I just tried your sript and works just fine at me, the metasploit framework installation opens normally
Linux MaD-pc 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
Really?! I am stumped then. I've come to the conclusion I'm missing some dependency on my installation that prohibits me from using .run files! I downloaded the full, mini, 32-bit, and 64-bit frameworks directly from Metasploit's website. And couldn't run any of them by clicking or using the terminal. (I'm on a 64-bit laptop, but have both libraries installed)

---

### Post by ja660k on 2011-06-11
> **GrantStoner said:**
> I'm working on a personal script to install a complete arsenal of pentest tools.

why dont you just use a pentesting os?
[http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)  -or-
[http://www.blackbuntu.com/](http://www.blackbuntu.com/)

---

### Post by GrantStoner on 2011-06-11
Because I don't need 300 tools. I need a few good ones. And I'd much rather just keep my script up to date and always have the latest and greatest. I find a lot of clutter on pre-built OSes. I like to keep it minimal and just have what I want/need.

On another note, if you're going to recommend distros/spins, only recommend THE BOSS.
For pentesting, THE BOSS is Back|Track - and none other. ;P
All those other distros are just "wanna be" distros.

---

### Post by hakermania on 2011-06-11
I don't think so that you're missing something, not sure on the other hand. Please, tell me what happens if you
1) make the file executable
2) double click it
3) click 'Run' if available.

If it runs OK then try normally (from the terminal, without running a script)
1) Download the metasploit with wget
2) Make it executable and run ./framework*
if on the other hand it doesn't run normally, then, yes, you're missing something :/


we have to find WHAT is responsible for this

---

### Post by BkkBonanza on 2011-06-11
Can you run an executable with a wildcard in the name? Shouldn't it specify the fully resolved name? I'm not sure but it seems like that may be a problem. The simplest thing is to test it manually at the prompt, either way.

For this I would create an array at the top with the filenames you want to dl/install and then use the menu to select which array element you do. That way you can easily add/chg names and you only need one bit of run code rather than a case stmnt.

Actually an array with (menu entry, src url, filename) sets might be nice then multiply menu value by 3. I guess that assumes the other installs are similar enough to this one, ie. d/l and run the file.

---

### Post by GrantStoner on 2011-06-11
> **hakermania said:**
> I don't think so that you're missing something, not sure on the other hand. Please, tell me what happens if you
1) make the file executable
2) double click it
3) click 'Run' if available.

If it runs OK then try normally (from the terminal, without running a script)
1) Download the metasploit with wget
2) Make it executable and run ./framework*
if on the other hand it doesn't run normally, then, yes, you're missing something :/


we have to find WHAT is responsible for this

Downloaded the file, made it executable, but when I double clicked it - nothing happened, not a single thing. When I right-clicked and hit "Open" - still nothing happens (no dialog pops up to Run or anything). chmod +x and changed to 777 and still nothing.

> **BkkBonanza said:**
> Can you run an executable with a wildcard in the name? Shouldn't it specify the fully resolved name? I'm not sure but it seems like that may be a problem. The simplest thing is to test it manually at the prompt, either way.

For this I would create an array at the top with the filenames you want to dl/install and then use the menu to select which array element you do. That way you can easily add/chg names and you only need one bit of run code rather than a case stmnt.

Actually an array with (menu entry, src url, filename) sets might be nice then multiply menu value by 3. I guess that assumes the other installs are similar enough to this one, ie. d/l and run the file.

I have already stated I tried with the fill name and path. And I said I have already tested manually in the terminal. As far as what you mean with creating the menu with an array, could you expand on this? I hate using case but I wasn't sure of another way to do it. And mind you - this is version 1 of like 1931093 to come. >_< By the time it's done this script won't look anything like the original - hopefully! But yes, how could I create the menu with an array? And how would I loop it back if any other random keys were hit?

---

### Post by BkkBonanza on 2011-06-11
> **GrantStoner said:**
> 
I have already stated I tried with the fill name and path. 

Sorry, must have just missed that.

> **GrantStoner said:**
> 
But yes, how could I create the menu with an array? And how would I loop it back if any other random keys were hit?

Something along this lines,
```

# define the options for installing as array of triples
PKGS=("Metasploit" "http://blah/blah" "framework-3.4.5-blah" 
      "S.E.T" "http://more/blah" "morework-3.4.5-blah" 
)

# output menu
echo "Now you've got some options!"
for x in `seq 0 ${#PKGS[@]}/3-1`; do
  echo "$x) Grab and install ${PKGS[($x*3)]}?"
done
read -p "(Enter a # to continue with it): " -n1 variable

# do the install for selected option
wget ${PKGS[$variable*3+1]}/${PKGS[$variable*3+2]}
chmod +x ./${PKGS[$variable*3+2]}
./${PKGS[$variable*3+2]}
rm -rf ${PKGS[$variable*3+2]}


```

Or something close. I didn't check syntax here and it's likely the math bits need extra ()'s to work right. 

You could add a function name as 4th element in array and then each pkg could be associated with a function to call if they don't all get installed the same way. Then you would put that wget & install in a function that gets called with name from array.

I didn't make this robust - you should check the variable is in range. Maybe some other minor fixes but this shows the idea.

You can also fill the array from a file instead that acts as a pkg list.
That can be done with one line with read command. It can read a file into array directly. See **man bash**.

---

### Post by GrantStoner on 2011-06-12
> **BkkBonanza said:**
> 
Something along this lines,
```

# define the options for installing as array of triples
PKGS=("Metasploit" "http://blah/blah" "framework-3.4.5-blah" 
      "S.E.T" "http://more/blah" "morework-3.4.5-blah" 
)

# output menu
echo "Now you've got some options!"
for x in `seq 0 ${#PKGS[@]}/3-1`; do
  echo "$x) Grab and install ${PKGS[($x*3)]}?"
done
read -p "(Enter a # to continue with it): " -n1 variable

# do the install for selected option
wget ${PKGS[$variable*3+1]}/${PKGS[$variable*3+2]}
chmod +x ./${PKGS[$variable*3+2]}
./${PKGS[$variable*3+2]}
rm -rf ${PKGS[$variable*3+2]}


```
I spent all day trying to make this array thing work. Research and research and more research. I couldn't get it to work like a charm.

I ended up re-writing pretty much all of it.
Now it looks like this:
```

#! /bin/bash

initializeANSI()
{
    esc=""
    
    blackf="${esc}[30m";    redf="${esc}[31m";    greenf="${esc}[32m"
    yellowf="${esc}[33m";    bluef="${esc}[34m";    purplef="${esc}[35m"
    cyanf="${esc}[36m";        whitef="${esc}[37m"
    
    blackb="${esc}[40m";    redb="${esc}[41m";    greenb="${esc}[42m"
    yellowb="${esc}[43m";    blueb="${esc}[44m";    purpleb="${esc}[45m"
    cyanb="${esc}[46m";        whiteb="${esc}[47m"
    
    reset="${esc}[0m"
}

# menu functions
metasploit()
{
    echo -e "\nInstalling Metasploit . . .\n"; sleep 1
    echo -e "Checking out the latest version . . .\n"
    svn co https://www.metasploit.com/svn/framework3/trunk/ /pentest/metasploit >/dev/null 2>~/Error\ Log.txt
    echo -e "Installing dependencies for Metasploit . . .\n"
    yum -y install ruby rubygems >/dev/null 2>~/Error\ Log.txt
    echo -e "Metasploit installed . . .\n"
}

s.e.t.()
{
    echo -e "\nInstalling Social-Engineer Toolkit . . .\n"; sleep 1
    echo -e "Checking out the latest version . . .\n"
    svn co http://svn.secmaniac.com/social_engineering_toolkit /pentest/set/ >/dev/null 
    echo -e "Installing dependencies and setting up S.E.T. . . .\n"
    chmod +x /pentest/set/setup.py
    /pentest/set/./setup.py install >/dev/null 2>~/Error\ Log.txt
    echo -e "\nS.E.T. installed . . .\n"
}

fasttrack()
{
    echo -e "\nInstalling FastTrack . . .\n"
    sleep 1
    svn co http://svn.secmaniac.com/fasttrack /pentest/fasttrack/
}

aircrack-ng()
{
    echo -e "\nInstalling Aircrack-ng . . .\n"
    sleep 1
}

clear

if [ "$UID" != "0" ]
then
    printf "\nRe-running as 'root'... "
    exec su -c $0
fi

initializeANSI
cat << EOF
${greenf}                       ,
                      dM
                      MMr
                     4MMML                  .
                     MMMMM.                xf
     .              "M6MMM               .MM-
      Mh..          +MM5MMM            .MMMM
      .MMM.         .MMMMML.          MMMMMh
${yellowf}       )MMMh.        MM5MMM         MMMMMMM
        3MMMMx.     'MMM3MMf      xnMMMMMM"
        '*MMMMM      MMMMMM.     nMMMMMMP"
          *MMMMMx    "MMM5M\    .MMMMMMM=
           *MMMMMh   "MMMMM"   JMMMMMMP
             MMMMMM   GMMMM.  dMMMMMM            .
              MMMMMM  "MMMM  .MMMMM(        .nnMP"
   ..          *MMMMx  MMM"  dMMMM"    .nnMMMMM*
${redf}    "MMn...     'MMMMr 'MM   MMM"   .nMMMMMMM*"
     "4MMMMnn..   *MMM  MM  MMP"  .dMMMMMMM""
       ^MMMMMMMMx.  *ML "M .M*  .MMMMMM**"
          *PMMMMMMhn. *x > M  .MMMM**""
             ""**MMMMhx/.h/ .=*"
                      .3P"%....
                    nP"     "*MMnx    ${reset}
EOF
echo -e "\E[32m~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"; tput sgr0
echo -e ${yellowb}${redf}"I'm going to be doing a lot of ****, SO JUST BE PATIENT!"${reset}
echo -e "\E[32m~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n"; tput sgr0
sleep 1

echo -e "Checking for a suitable SVN client . . ."; sleep 1
rpm -q subversion >/dev/null 2>~/Error\ Log.txt
if [ "$?" != "0" ]
then
    echo -e "No suitable SVN package installed. Grabbing one now . . .\n";
    yum -y install subversion >/dev/null 2>~/Error\ Log.txt
else
    echo -e "Dependencies met. Continuing on . . .\n"; sleep 1
fi

# menu start
while :
do
    cat << EOF
${greenf}H A X 0 R - T O O L - M E N U

1. Metasploit
2. Social-Engineer Toolkit
3. FastTrack
4. Aircrack-ng
5. Quit
EOF

echo -n -e "\nType a # and hit [ENTER]: "${reset}
read choice

case $choice in
     1) metasploit ;;
     2) s.e.t. ;;
     3) fasttrack ;;
     4) aircrack-ng ;;
     5) echo && exit ;;
     *) echo -e "\n\"$choice\" is not valid!\n"
esac
done

exit 0

```Feel free to test it, I've only tested Metasploit. S.E.T. is from my old one, so I don't know if it works - haven't tested it. All the others are incomplete still. But feel free to test Metasploit! The only thing is, make sure subversion is installed. AND comment out the part where it searches for subversion - it only works on Fedora cause it searches the rpm database.

EDIT: I changed it real quick and attached it. All you need to do is run it if subversion is installed. :)

---

### Post by hakermania on 2011-06-12
> **BkkBonanza said:**
> Can you run an executable with a wildcard in the name? Shouldn't it specify the fully resolved name? I'm not sure but it seems like that may be a problem. The simplest thing is to test it manually at the prompt, either way.
I just tested, it works fine!

Also, I fully run his script and again, it works fine!

---

