---
title: "Bash Script, stopping the stops"
date: 2015-01-08
forum: Programming Talk
---

### Post by keyxmakerx2 on 2015-01-08
I am defently a noob when it comes to scripting. I have wrote my own bash script, using just basic apt-get and app armor commands to allow for a easy setup. But during the script there are (Do you want to continue Y/n)  which stops the script requiring an answer,is there any way to ignore and auto Y this? Also the Press enter to add rep. Also when there are sometimes on newer versions, apps that don't pull over. So There is an error that it can't find the package, which stops the script completely. Is there any way to fix this as well?Thanks :)Here is the Code [https://github.com/keyxmakerx/Setup](https://github.com/keyxmakerx/Setup)

---

### Post by kerry_s on 2015-01-08
sudo apt-get update <-make sure your getting new version
sudo apt-get -y install <- auto yes

---

### Post by Vaphell on 2015-01-08
code would be nice

---

### Post by keyxmakerx2 on 2015-01-08
Sorry typed this up at the last minute before work. :) Here is my link, 

[https://github.com/keyxmakerx/Setup](https://github.com/keyxmakerx/Setup)

---

### Post by keyxmakerx2 on 2015-01-08
> **kerry_s said:**
> sudo apt-get update <-make sure your getting new version
sudo apt-get -y install <- auto yes

How about when adding repositorys?

---

### Post by CantankRus on 2015-01-09
```
man add-apt-repository
```

> SYNOPSIS

add-apt-repository [OPTIONS] REPOSITORY  
DESCRIPTION

add-apt-repository is a script which adds an external APT repository to either /etc/apt/sources.list or a file in /etc/apt/sources.list.d/ or removes an already existing repository.
The options supported by add-apt-repository are:

-h, --help Show help message and exit

-m, --massive-debug Print a lot of debug information to the command line

-r, --remove Remove the specified repository

[COLOR="#FF0000"]**-y, --yes Assume yes to all queries**[/COLOR]

-k, --keyserver Use a custom keyserver URL instead of the default

-s, --enable-source Allow downloading of the source packages from the repository

---

### Post by keyxmakerx2 on 2015-01-09
> **CantankRus said:**
> ```
man add-apt-repository
```


Awesome! now last thing I promise :) How do I get it to not stop when theres an error, and if possible make an error log file for it.

---

### Post by nerdtron on 2015-01-09
> **keyxmakerx2 said:**
>  How do I get it to not stop when theres an error, and if possible make an error log file for it.

How not to stop it regardless of errors? That depends on how your script is written.
As for the log file. You can just redirect the output of the script to another file like this

```
bash /this/is/my/script > log.txt
```
You can see more example here: [http://www.cyberciti.biz/faq/howto-save-ouput-of-linux-unix-command-to-file/](http://www.cyberciti.biz/faq/howto-save-ouput-of-linux-unix-command-to-file/)

Also have you tried running the script as "bash -x /my/script/here"? The -x will show you which commands are executed by the script.

---

### Post by keyxmakerx2 on 2015-01-10
> **nerdtron said:**
> How not to stop it regardless of errors? That depends on how your script is written.
As for the log file. You can just redirect the output of the script to another file like this

```
bash /this/is/my/script > log.txt
```
You can see more example here: [http://www.cyberciti.biz/faq/howto-save-ouput-of-linux-unix-command-to-file/](http://www.cyberciti.biz/faq/howto-save-ouput-of-linux-unix-command-to-file/)

Also have you tried running the script as "bash -x /my/script/here"? The -x will show you which commands are executed by the script.


Thanks :) But I knew how to do that. I'm trying to make a script anyone would be able to run, and want to make it independent from the terminal eventually. Is there a way to add this to the script itself?

---

### Post by keyxmakerx2 on 2015-01-10
(Solved Issue)

---

### Post by nerdtron on 2015-01-10
> Is there a way to add this to the script itself?

Something like this:
```

#!/bin/bash
#Declare the log file
LOGFILE=/path/to/log.txt

#your commands here:
sudo apt-get update 2&>1 $LOGFILE
sudo apt-get upgrade 2&>1 $LOGFILE

```

---

### Post by schragge on 2015-01-11
> **keyxmakerx2 said:**
> Another problem I've been happening which correlates with the error stops. Is that if there is a line of code, and one thing is not in the repository anymore, it will skip all "installs" for some reason.
Because you explicitly ask the script to do so. The sequence **&&\** at the end of each line means precisely this: continue only if the previous command succeeded.

---

### Post by keyxmakerx2 on 2015-01-15
Is there any way of doing it differently? That was the only way I knew how to do it. :)

---

### Post by keyxmakerx2 on 2015-01-15
Thanks for your help, i'll add that now :)

---

### Post by schragge on 2015-01-15
> **keyxmakerx2 said:**
> Is there any way of doing it differently?
```
set -e
``` But it's not quite the same, see [The Set Builtin]("https://www.gnu.org/software/bash/manual/html_node/The-Set-Builtin.html") and [http://mywiki.wooledge.org/BashFAQ/105](http://mywiki.wooledge.org/BashFAQ/105)

---

### Post by keyxmakerx2 on 2015-01-15
So it would be  ```
set -e  apt-get update  apt-get upgrade
```

---

### Post by schragge on 2015-01-15
No, it would be
 ```

set -e
apt-get update
apt-get upgrade

```
But you should really read the links I gave above to fully understand implications of using *set -e*. The setting will stay active for the rest of the script, or until you explicitly set it off with *set +e*. Besides, you got it wrong. *set -e* will do the opposite of what you want: it will abort the script on the first command that returns with an error. To *continue* execution despite errors you should remove all the **&&\** from your script.

BTW, this is wrong:
```
[COLOR=blue]command_1[/COLOR] &&\ 2&>1 $LOGFILE
[COLOR=blue]command_2[/COLOR]

```
If you want to redirect both standard error and standard output streams of [COLOR=blue]command_1[/COLOR] to $LOGFILE then it should be
```

[COLOR=blue]command_1[/COLOR] [COLOR=red]>"[/COLOR]$LOGFILE[COLOR=red]"[/COLOR]  2>&1 &&[COLOR=red]\[/COLOR]
[COLOR=blue]command_2[/COLOR]

```
Note the parts I marked in [COLOR=red]red[/COLOR]. 1) Don't forget the redirect operator ([COLOR=red]>[/COLOR]); 2) Quote the variable as the logfile name may contain whitespace; 3) Backslash ([COLOR=red]\[/COLOR]) must be the last character in the line to act as continuation mark.

Bash has a non-standard and non-portable shortcut for redirecting both stderr and stdout to a file:
```

[COLOR=blue]command_1[/COLOR] &>"$LOGFILE"

```
in bash is the same as
```

[COLOR=blue]command_1[/COLOR] >"$LOGFILE"  2>&1

```
This shortcut doesn't work in other POSIX shells.

---

### Post by keyxmakerx2 on 2015-01-16
So I should remove the &&\ to continue without error stops, which I would then just leave them blank.

I should remove the current way I thought of the log filing, and instead insert [COLOR=#000000][FONT=Ubuntu Mono]&>"$LOGFILE"  which, would I leave logfile as that name, or change it to the name of the file it's being saved to?

I did read the links, I just didn't understand them.. I'm not a programmer, just a wanna be server admin :)[/FONT][/COLOR]

---

### Post by schragge on 2015-01-16
> **keyxmakerx2 said:**
> So I should remove the &&\ to continue without error stops, which I would then just leave them blank.
Yep.

> I should remove the current way I thought of the log filing, and instead insert &>"$LOGFILE"
Either this or *>"$LOGFILE" 2>&1*

> which, would I leave logfile as that name, or change it to the name of the file it's being saved to?
*$LOGFILE* is not the name of logfile, it's just a variable that logfile name happens to be kept in. At the beginning of your script, you assign this variable with
```
LOGFILE=/usr/scriptlog.txt
```
BTW, saving the logfile under */usr/* goes against the [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"). Standard place to put logfiles in is */var/log/*.

---

### Post by keyxmakerx2 on 2015-01-19
Okay I've updated it with the information provided. Thanks again. I am going to open a KVM and see how it goes :)

---

### Post by keyxmakerx2 on 2015-01-20
since i've got such great help, i might as well see how hard i can push it XD I've tried to setup a question asking would you like to run this script. Which actually works too well. it only asks and doesn't actually stop the script if you say no. Is there a way I could get it to ask the client y or no and actually work, and if so, could it also ask what type of computer, that way I could setup multiple scripts for different people. If you guys know of a good tutorial or anything thats fine, i tried to look it up, but i guess my googlefu isn't as strong.

---

### Post by keyxmakerx2 on 2015-01-20
(Fixed)

---

### Post by Vaphell on 2015-01-20
relevant code would be nice

---

### Post by keyxmakerx2 on 2015-01-20
> **Vaphell said:**
> relevant code would be niceThere is a comment with the link to github in it? Is that what you are referring to?

---

### Post by Vaphell on 2015-01-21
well, indeed it is ... on page 1 of 3 and not in the first post so one has to scroll down to see it if one is not current. You could paste that read + case here to spare people legwork.

the script is a redundant mess. It's literally begging for few loops. Also you should get rid of all sudos and just run the script with it and complain that root is needed.


```
#!/bin/bash

(( UID != 0 )) && { echo "Run the script as root"; exit 1; }

LOGFILE=........

ppas=( 
       ppa:nowrep/qupzilla                      ppa:sukso96100/budgie-desktop
       ppa:webupd8team/haguichi                 ppa:daniel.pavel/solaar
       ppa:nuvola-player-builders/stable        ppa:appgrid/stable
       ppa:dhor/myway                           ppa:hikariknight/unix-runescape-client
       ppa:atareao/atareao                      ppa:ffmulticonverter/stable
       ppa:peterlevi/ppa                        ppa:teejee2008/ppa
       ppa:deluge-team/ppa                      ppa:asukhovatkin/unity-launcher-folders
       ppa:the-duck/launcher                    ppa:shnatsel/dnscrypt
       ppa:danielrichter2007/grub-customizer    ppa:george-edison55/george-edison
       ppa:samrog131/ppa                        ppa:ubuntu-wine/ppa
       ppa:n-muench/burg                        ppa:nilarimogard/webupd8
       ppa:samrog131/ppa                        ppa:webupd8team/tribler
       ppa:webupd8team/y-ppa-manager            ppa:me-davidsansome/clementine
       ppa:wfg/0ad.dev
     )

declare -A add_ppas=( 
                      ["unvanquished"]="http://debs.unvanquished.net trusty main"
                      ["owncloud-client"]="http://download.opensuse.org/repositories/home:/colomboem/xUbuntu_14.10/ /"
                      ["dukto"]="http://download.opensuse.org/repositories/isv:/ownCloud:/community:/testing/xUbuntu_14.04/ /"                     
                    )

packages=(
           uget
           indicator-multiload qupzilla
           filezilla
           unvanquished
           haguichi haguichi-appindicator
           konqueror diodon diodon-plugins gsmartcontrol
           dukto tree appgrid
           nuvolaplayer
           google-chrome-unstable
           conky-all hddtemp
           vlc xbmc
           wine1.7 nmon htop 
           duck-launcher 
           ubuntu-restricted-extras 
           geary bacula git openshot mosh deluge 
           icedtea-7-plugin openjdk-7-jre openjdk-7-jdk unix-runescape-client 
           unity-tweak-tool qemu-kvm 
           libvirt-bin 
           variety openssh-server openssh-client mosh 
           ftp bridge-utils virt-manager minitube 
           dnscrypt-proxy 
           conky-manager 
           unity-launcher-folders 
           0ad 
           gufw burg burg-themes 
           y-ppa-manager 
           ubuntu-vm-builder 
           tribler 
           clutter-gtk-1.0 mx-1.0 
           indicator-cpufreq traceroute photoqt screen 
           keybinder-3.0 gee-0.8 
           libnspr4-0d guake git gimp cmake 
           syncwall 
           terminator clementine 
           libxml2-dev 
         )

# --- start -------------------

while :
do
    read -p "Continue? y/n " choice
    case ${choice,,} in
        y|ye|yes) break;;
        n|no) echo "Bye!"; exit;;
    esac
done

{
    for ppa in "${ppas[@]}"
    do
        add-apt repository -a "$ppa"
    done

    for add in "${!add_ppas[@]}"
    do
        echo "deb ${add_ppas[$add]}" >> "/etc/apt/sources.list.d/$add.list"
    done

    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9BA73CFA
    wget http://debs.unvanquished.net/unvanquished-archive-key.gpg.asc
    apt-key add unvanquished-archive-key.gpg.asc

    apt-get update && sudo apt-get autoremove

#    apt-get install "${packages[@]}"  # everything at once

    for pkg in "${packages[@]}"
    do
        apt-get install "$pkg"
    done

# etc
# etc
# etc 

} &>"$LOGFILE"

```

---

### Post by ofnuts on 2015-01-21
> **Vaphell said:**
> Also you should get rid of all sudos and just run the script with it and complain that root is needed.

I agree with that, even if a string of sudo's isn't that bad, because only the first one is going to ask for a password.

Another solution, start the script with something like
```

[[ $(id --user) -ne 0 ]] && { echo "Sudoing..." ; sudo $(readlink -e $0) $* ; exit 0 ; } # sudo ourself

```

---

### Post by Vaphell on 2015-01-21
> ```
sudo $(readlink -e $0) $* 
```

that should be
```
sudo $(readlink -e $0) "$@"
```

$* is destructive if there are relevant non-delimiting whitespaces inside params as it glues everything into a single string using IFS[0] destoying original param split.
For params 'a' 'b c' 'd e f' you will get either 'a b c d e f' (if quoted $*) or 'a' 'b' 'c' 'd' 'e' 'f' (if unquoted $* because  wordsplitting as stage 2)
The only thing that preserves params (and arrays) is "$@" ("${arr[@]}")

```
$ test() { printf -- '%s\n' "$*" '---'; printf -- '%s\n' $* '---'; printf -- '%s\n' "$@"; }
$ test 'a' 'b c' 'd e f'
a b c d e f
---
a
b
c
d
e
f
---
a
b c
d e f
```

---

### Post by keyxmakerx2 on 2015-01-21
Okay, so the one vaphell suggested only asked you to run as sudo, while ofnuts actually lets you run as root?                                                                                                                                                                So I would use ```
 [[ $(id --user) -ne 0 ]] && { echo "Sudoing..." ; sudo $(readlink -e $0) "$@" ; exit 0 ; } # sudo ourself    
```                                     -Because that  groups up the commands correctly?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Okay so I'm seeing now how it's done, So, you basically name the sections of ppas, and packages and group them together to be installed. Is there a way I could make multiple scripts and have a script that will ask for which script to run?

---

### Post by keyxmakerx2 on 2015-01-21
(Fixed) I had a script blocker turned on.

---

### Post by Vaphell on 2015-01-21
> Okay, so the one vaphell suggested only asked you to run as sudo, while ofnuts actually lets you run as root? So I would use
Code:

```
[[ $(id --user) -ne 0 ]] && { echo "Sudoing..." ; sudo $(readlink -e $0) "$@" ; exit 0 ; } # sudo ourself
```

yes
this code spawns another instance of the script with sudo in front so it gets necessary privileges.


add *lib32z1 lib32ncurses5 lib32bz2-1.0 gdebi-core* to package array too. That's what's it for, so you don't have to have no other
redundant *sudo apt-get install X*, the array + loop take care of that.


if you have a bunch of the same crap with only a tiny bit changing, it's a sign you need to parametrize it, have a loop.

---

### Post by keyxmakerx2 on 2015-01-21
Okay, so I fixed the orphan you were talking about. I think.

So.. Will this work for making a script that will ask which script to run?
```
 while:
[TABLE="class: highlight tab-size-8 js-file-line-container"]
[TR]
[TD="class: blob-code js-file-line"][COLOR=#A71D5D]do[/COLOR][/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code js-file-line"]    [COLOR=#0086B3]read[/COLOR] -p [COLOR=#DF5000]"Which computer are you installing on? 1)Personal 2)Gaming 3)Server "[/COLOR] choice[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code js-file-line"]    [COLOR=#A71D5D]case[/COLOR] ${choice,,} in[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code js-file-line"]        P|Person|Personal) [COLOR=#0086B3]./runp[/COLOR];; #runp will be the name of the personal computer setup?[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code js-file-line"]        G|Gaming) ./rung;;
[COLOR=#0086B3]        S|Server)[/COLOR] [COLOR=#0086b3]./runs[/COLOR];;[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code js-file-line"]    [COLOR=#A71D5D]esac[/COLOR][/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code js-file-line"][COLOR=#A71D5D]done[/COLOR][/TD]
[/TR]
[/TABLE]


```

---

### Post by schragge on 2015-01-21
Since you're using bash anyway, have you looked into possibility of using [select]("http://www.gnu.org/software/bash/manual/html_node/Conditional-Constructs.html#index-select") for it? It's less flexible than a *while* loop with *read*, but may be adequate for you needs. [Here]("http://tldp.org/LDP/abs/html/testbranch.html#SELECTREF") is an example of how to use *select*.

---

### Post by Vaphell on 2015-01-21
it's not
```
while:
```
it's
```
while :
```
shells are whitespace sensitive. : is an empty operation, a no-op that happens to always be successful, so that line means*while <always true>*

also you will never leave the infinite *while true* loop because you have no *break* that would make the script jump out of it.

*read -p "... " choice* can be augmented with -n1 to read only 1 character so you don't have to type whole words increasing the risk of typos significantly

```
while :
do
    read -n1 -p "[P]ersonal [G]aming [S]erver ?   " choice
    echo
    case ${choice^} in
        P) ./runp;;
        G) ./rung;;
        S) ./runs;;
        *) continue;;
    esac
    break
done
```

ps. in that pretty table *done* should be paired with *do* ;-)

---

### Post by keyxmakerx2 on 2015-01-21
My brain is fried.. 

schragge. I looked at the webpage, I'll be honest, I don't know what a loop is. But after seeing your example, i would have to do a section for every option, because I want the choice of personal and server mostly. 

Vaphell, Okay, I copied that from github, that's why the table is there. But can you elaborate on the "read -p -n1" im guessing the -p just means pause, but-n1 means it will only read the [ebracted] letters?

P.S. changed logo because i like it, im not anon or anything. XD

---

### Post by Vaphell on 2015-01-21
> read -p -n1" im guessing the -p just means pause,

no, -p means prompt, ie the message shown to the user ( "personal/gaming/server" ).

>  but-n1 means it will only read the [ebracted] letters?

no, it reads a single char (-n <how many chars>) without waiting for enter which produces a hotkey-like behavior and $choice is guaranteed to store a single char which simplifies case tests. In the code the * clause matches any garbage and *continue *forces retry (another while loop iteration) until one of PGS is hit.
Just copy-paste the snippet into terminal (ctrl+c/ctrl+shift+v) and see how it works.

---

### Post by keyxmakerx2 on 2015-01-22
How would i set it up to ask for you to install an application. Say if you installing the server version, it will ask you if you want to install a LEMP server. 

So would it be, 
```

while :
do
    read -n1 -p "Do you want to install LEMP [Y]es [N]o  " choice
    echo
    case ${choice^} in
Y) [COLOR=#111111][FONT=monospace]sudo apt-get install nginx, [/FONT][/COLOR][COLOR=#111111][FONT=monospace]mysql-server[/FONT][/COLOR];;
N) continue;;
        *) continue;;
    esac
    break
done

```

---

### Post by Vaphell on 2015-01-22
for clarity and separation of concerns you can outsource the code to functions and remember that your script is with sudo rights already.

```
lemp_install()
{
  echo "installing LEMP...."
  apt-get install nginx mysql-server       <- no sudo here because the script runs with it
}

while :
do
    read -n1 -p "Do you want to install LEMP [Y]es [N]o  " choice
    echo
    case ${choice^} in
        Y) lemp_install;;
        N) continue;;          <- this will restart the LEMP question, if you want to move beyond the loop on N you need break
        *) continue;;
    esac
    break
done
```

---

### Post by keyxmakerx2 on 2015-01-22
I played with it to make sure I understand this correctly. 
```

PhP()
 {
  php5-fpm php5-mysql
 }
 lemp_install()
{
  echo "installing LEMP...."
  apt-get install nginx mysql-server
  mysql_install_db
  mysql_secure_installation
   for ppa in "${PhP[@]}"
    do
        apt-get install -a "$pkg"
    done
}


while :
do
    read -n1 -p "Do you want to install LEMP [Y]es [N]o  " choice
    echo
    case ${choice^} in
        Y) lemp_install;;
        N) break;;          #<- this will restart the LEMP question, if you want to move beyond the loop on N you need break
        *) continue;;
    esac
    break
done

```

---

### Post by Vaphell on 2015-01-22
this is a [COLOR="#008000"]function[/COLOR], a "mini-script", which doesn't even make sense because it would attempt to execute program 'php5-fpm' with a 'php5-mysql' param.
```
PhP[COLOR="#008000"]()[/COLOR]
[COLOR="#008000"] {[/COLOR]
  php5-fpm php5-mysql
  # command  param(s)
[COLOR="#008000"] }[/COLOR]
```

this is an [COLOR="#800080"]array[/COLOR], a data structure that can be iterated over, with 2 elements 
```
PhP=[COLOR="#800080"]([/COLOR] php5-fpm php5-mysql [COLOR="#800080"])[/COLOR]
```


the loop variable should be used within a loop somewhere in order for the loop to make any sense, in this case the blue parts should match 
```
for [COLOR="#0000FF"]pkg[/COLOR] in "${PhP[@]}"
    do
        apt-get install -a "[COLOR="#0000FF"]$pkg[/COLOR]"
    done
```


you should get familiar with some bash basics.

---

### Post by keyxmakerx2 on 2015-01-22
Okay, so part of configuring the PhP is editing a file, is there a way to change the file via bash?

sudo nano /etc/php5/fpm/php.ini
[COLOR=#000000][FONT=proxima-nova]What we are looking for in this file is the parameter that sets cgi.fix_pathinfo. This will be commented out with a semi-colon (;) and set to "1" by default.

[/FONT][/COLOR]
cgi.fix_pathinfo=0

---

### Post by schragge on 2015-01-23
```

inifile=/etc/php5/fpm/php.ini
if grep -qw 'cgi\.fix_pathinfo' "$inifile"
then
    sed -i 's/^[ \t;]*\(cgi\.fix_pathinfo\)[ \t]*=.*/\1=0/' "$inifile"
else
    echo 'cgi.fix_pathinfo=0' >>"$inifile"
fi

```

---

### Post by keyxmakerx2 on 2015-01-23
> **schragge said:**
> ```

inifile=/etc/php5/fpm/php.ini
if grep -qw 'cgi\.fix_pathinfo' "$inifile"
then
    sed -i 's/^[ \t;]*\(cgi\.fix_pathinfo\)[ \t]*=.*/\1=0/' "$inifile"
else
    echo 'cgi.fix_pathinfo=0' >>"$inifile"
fi

```

I'll be honest, i've been looking at this for 15 min, and i can't understand heads or tails. So lets say i need to edit something else, what would I change?

---

### Post by Vaphell on 2015-01-23
```
if grep -qw 'cgi\.fix_pathinfo' "$inifile"       # if looking for 'cgi.fix_pathinfo' in $inifile is successful
then
    sed -i '[COLOR="#FF0000"]s/[/COLOR][COLOR="#800080"]^[/COLOR][COLOR="#40E0D0"][ \t;]*[/COLOR][COLOR="#008000"]\(cgi\.fix_pathinfo\)[/COLOR][COLOR="#FFA500"][ \t]*[/COLOR][COLOR="#DDA0DD"]=.*[/COLOR][COLOR="#FF0000"]/[/COLOR][COLOR="#008000"]\1[/COLOR]=0[COLOR="#FF0000"]/[/COLOR]' "$inifile"
    # [COLOR="#FF0000"]replace [/COLOR]
    # [COLOR="#800080"]start-of-line[/COLOR][COLOR="#40E0D0"]{0-or-more '',\t,;}[/COLOR][COLOR="#008000"](cgi.fix_pathinfo)[/COLOR][COLOR="#FFA500"]{0-or-more whitespace}[/COLOR][COLOR="#DDA0DD"]={whatever}[/COLOR]
    # [COLOR="#FF0000"]with[/COLOR]
    # [COLOR="#008000"]parenthesized part[/COLOR]=0
                                                                                                   
else
    echo 'cgi.fix_pathinfo=0' >>"$inifile"   # append 'cgi.fix_pathinfo=0'
fi
```

google, seriously.

---

### Post by keyxmakerx2 on 2015-01-23
> **Vaphell said:**
> ```
if grep -qw 'cgi\.fix_pathinfo' "$inifile"       # if looking for 'cgi.fix_pathinfo' in $inifile is successful
then
    sed -i '[COLOR=#FF0000]s/[/COLOR][COLOR=#800080]^[/COLOR][COLOR=#40E0D0][ \t;]*[/COLOR][COLOR=#008000]\(cgi\.fix_pathinfo\)[/COLOR][COLOR=#FFA500][ \t]*[/COLOR][COLOR=#DDA0DD]=.*[/COLOR][COLOR=#FF0000]/[/COLOR][COLOR=#008000]\1[/COLOR]=0[COLOR=#FF0000]/[/COLOR]' "$inifile"
    # [COLOR=#FF0000]replace [/COLOR]
    # [COLOR=#800080]start-of-line[/COLOR][COLOR=#40E0D0]{0-or-more '',\t,;}[/COLOR][COLOR=#008000](cgi.fix_pathinfo)[/COLOR][COLOR=#FFA500]{0-or-more whitespace}[/COLOR][COLOR=#DDA0DD]={whatever}[/COLOR]
    # [COLOR=#FF0000]with[/COLOR]
    # [COLOR=#008000]parenthesized part[/COLOR]=0
                                                                                                   
else
    echo 'cgi.fix_pathinfo=0' >>"$inifile"   # append 'cgi.fix_pathinfo=0'
fi
```

google, seriously.

I tried googling, and I got documentation on the program sed that I didn't understand. I've been studying it, but I'm very new at this, and not much of it makes sense to me yet.

Also the tutorial I'm using is this one. 
[https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux](https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux)
and trying them out on my c9.io account.

---

### Post by Vaphell on 2015-01-24
sed s/from/to/ = replace from pattern with to pattern
-i modify source file in place 

[http://www.regular-expressions.info](http://www.regular-expressions.info)
relevant topics:
anchor
character classes
dot
repetition
backreference

---

### Post by keyxmakerx2 on 2015-02-07
I know your glad to here im back. I'll be honest I've looked at so many web pages and video tutorials i feel like my head is about to explode. But the idea of learning regex is really intriguing to me. So I'm not giving up yet, I will say the website you sent me to though I wasn't able to understand at all. I don't know half of the words he's talking about, I guess Im just too noobie for it. Anyways, I have updated the script, and wanted to show you what I have so far, there are alot of comments where I will be adding more once I learn how to use sed and regex more. 

[https://github.com/keyxmakerx/Setup/blob/master/RunS.sh](https://github.com/keyxmakerx/Setup/blob/master/RunS.sh)

What's even better is im doing server overhall next weekend, so im hoping to have the script ready to go by then. Honestly, for the most part the stuff that's in it will do, I just would like to learn regex and sed so that I can add that manual security thats a part of it.

---

### Post by ofnuts on 2015-02-08
The best book on the subject: [www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124](www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124)

---

### Post by tjmarch on 2015-02-15
Can any one help I writing a script and the following will output desktop-session enviroment when used from command line but puts out nothing if used in a <script>.sh
with no faults just a blank line. Why ? Could use some help


echo "$XDG_CURRENT_DESKTOP" | { de=$(< /dev/stdin); echo "$de"; };

also tried

printf "$XDG_CURRENT_DESKTOP"\\r | { de=$(< /dev/stdin); echo "$de"; };

same problem


This is how I am using it file test.sh has content:

export nam=`who | cut -d' ' -f1 | sort | uniq`

echo "$XDG_CURRENT_DESKTOP" | { de=$(< /dev/stdin); echo "$de"; };
sed -i -e "s/xx/$de/g" /home/$nam/.xinitrc


File I am trying to edit is .xinitrc with content:

#!/usr/bin/
#
# Setting blacklist for etho r8169
export a=3.8-1-xenomai.x86-686-pae
export d=3.8-1-xenomai.x86-amd64
export ver=`uname -r`
export dsk=xx
export ck=''
echo "starting the X session, $dsk" >&2
export XAUTHORITY=/home/sysop/.Xauthority
if [ $ver != $a ];then
$ck=true
else
echo " "
fi
if [ $ver != $d ];then
$ck=true
else
echo " "
fi
if [ $ck = true ];then
cp /home/$nam/.blacklist.conf.x /etc/modprobe.d/blacklist.conf
else
cp /home/$nam/.blacklist.conf.org /etc/modprobe.d/blacklist.conf
fi
exec $dsk --with-ck-launch > /home/sysop/errors-boot.txt 2>&1


After running test.sh, file .xinitrc is edited to:

#!/usr/bin/
#
# Setting blacklist for etho r8169
export a=3.8-1-xenomai.x86-686-pae
export d=3.8-1-xenomai.x86-amd64
export ver=`uname -r`
export dsk=                       <-----------------------------------------------------------------------------This has changed but not to what I want
export ck=''
echo "starting the X session, $dsk" >&2
export XAUTHORITY=/home/sysop/.Xauthority
if [ $ver != $a ];then
$ck=true
else
echo " "
fi
if [ $ver != $d ];then
$ck=true
else
echo " "
fi
if [ $ck = true ];then
cp /home/$nam/.blacklist.conf.x /etc/modprobe.d/blacklist.conf
else
cp /home/$nam/.blacklist.conf.org /etc/modprobe.d/blacklist.conf
fi
exec $dsk --with-ck-launch > /home/sysop/errors-boot.txt 2>&1

---

### Post by ofnuts on 2015-02-15
Your pipe between the echo and the brace list implies that everything is run in a subprocess (one for echo, one for the sequence in braces). So your "de" variable gets initialized in the subprocess and this value is never set in the "main" process. I don't see the purpose of such a contrived expression... what is wrong with:
```

echo "$XDG_CURRENT_DESKTOP"
de=$(< /dev/stdin)
echo "$de"

```

or even better:
```

echo "$XDG_CURRENT_DESKTOP"
read de
echo "$de"

```

---

### Post by tjmarch on 2015-02-15
Thank you for the reply, I tried both of your solutions which also work from command line but not from within a script file
I also tried: But still no luck

#!/bin/sh
export nam=`who | cut -d' ' -f1 | sort | uniq`
echo "$XDG_CURRENT_DESKTOP" >&2
de=$(< /dev/stderr)
echo "$de"
sed -i -e "s/xx/$de/g" /home/$nam/.xinitrc

---

### Post by ofnuts on 2015-02-15
Then it could be useful to show us the whole script.

---

### Post by tjmarch on 2015-02-15
There are two files:
first file test.sh

#!/bin/sh
export nam=`who | cut -d' ' -f1 | sort | uniq`
echo "$XDG_CURRENT_DESKTOP"
de=$(< /dev/stdin)
sed -i -e "s/xx/$de/g" /home/$nam/.xinitrc


Second file .xinitrc

#!/usr/bin/
#
# Setting blacklist for etho r8169
export a=3.8-1-xenomai.x86-686-pae
export d=3.8-1-xenomai.x86-amd64
export ver=`uname -r`
export dsk=xx
export ck=''
echo "starting the X session, $dsk" >&2
export XAUTHORITY=/home/sysop/.Xauthority
if [ $ver != $a ];then
$ck=true
else
echo " "
fi &
if [ $ver != $d ];then
$ck=true
else
echo " "
fi
if [ $ck = true ];then
cp /home/$nam/.blacklist.conf.x /etc/modprobe.d/blacklist.conf
else
cp /home/$nam/.blacklist.conf.org /etc/modprobe.d/blacklist.conf
fi
exec $dsk --with-ck-launch > /home/sysop/errors-boot.txt 2>&1

First file edits the second file item:
xx

Which is on line number 7
export dsk=xx

---

### Post by tjmarch on 2015-02-15
There are two files:
first file test.sh

#!/bin/sh
export nam=`who | cut -d' ' -f1 | sort | uniq`
echo "$XDG_CURRENT_DESKTOP"
de=$(< /dev/stdin)
sed -i -e "s/xx/$de/g" /home/$nam/.xinitrc


Second file .xinitrc

#!/usr/bin/
#
# Setting blacklist for etho r8169
export a=3.8-1-xenomai.x86-686-pae
export d=3.8-1-xenomai.x86-amd64
export ver=`uname -r`
export dsk=xx
export ck=''
echo "starting the X session, $dsk" >&2
export XAUTHORITY=/home/sysop/.Xauthority
if [ $ver != $a ];then
$ck=true
else
echo " "
fi &
if [ $ver != $d ];then
$ck=true
else
echo " "
fi
if [ $ck = true ];then
cp /home/$nam/.blacklist.conf.x /etc/modprobe.d/blacklist.conf
else
cp /home/$nam/.blacklist.conf.org /etc/modprobe.d/blacklist.conf
fi
exec $dsk --with-ck-launch > /home/sysop/errors-boot.txt 2>&1

First file edits the second file item:
xx

Which is on line number 7
export dsk=xx


If you run first file:

sudo ./test.sh

The results for .xinitrc are:

#!/usr/bin/
#
# Setting blacklist for etho r8169
export a=3.8-1-xenomai.x86-686-pae
export d=3.8-1-xenomai.x86-amd64
export ver=`uname -r`
export dsk=       <-----------------------------------------------This is incorrect I am expecting      X-Cinnamon       on my machine,  your machine should put your desktop environment
export ck=''
echo "starting the X session, $dsk" >&2
export XAUTHORITY=/home/sysop/.Xauthority
if [ $ver != $a ];then
$ck=true
else
echo " "
fi &
if [ $ver != $d ];then
$ck=true
else
echo " "
fi
if [ $ck = true ];then
cp /home/$nam/.blacklist.conf.x /etc/modprobe.d/blacklist.conf
else
cp /home/$nam/.blacklist.conf.org /etc/modprobe.d/blacklist.conf
fi
exec $dsk --with-ck-launch > /home/sysop/errors-boot.txt 2>&1



In terminal if you paste the following you will get your desktop environment:

echo "$XDG_CURRENT_DESKTOP"

Why will it not work in script ?

---

### Post by tjmarch on 2015-02-15
Got it to work:p used the following for test.sh :

#!/bin/sh
export nam=`who | cut -d' ' -f1 | sort | uniq`
env | grep DESKTOP_SESSION=
de=$(< /dev/stderr)
sed -i -e "s/xx/$de/g" /home/$nam/.xinitrc

---

