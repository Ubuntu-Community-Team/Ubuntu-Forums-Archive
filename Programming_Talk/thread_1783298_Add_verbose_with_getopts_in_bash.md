---
title: "Add verbose with getopts in bash?"
date: 2011-06-15
forum: Programming Talk
---

### Post by GrantStoner on 2011-06-15
Here's what I've got:```
#! /bin/bash

usage()
{
    cat << EOF
    
Syntax: $0 --option
or
Syntax: $0 -o

OPTIONS:
    -h | --help    Show this message
    -v | --verbose    Verbose-mode

"This is Ground Controld to Major Tom:
You've really made the grade.
And the papers want to know whose shirts you wear.
Now it's time to leave the capsule if you dare."

EOF
}

verbose()
{
    VERBOSE=1
}

while getopts "h:v" OPTIONS ; do
    case ${OPTIONS} in
        h|-help) usage; exit
        ;;
        v|-verbose) verbose ;;
    esac
done

clear

if [ "$UID" != "0" ]; then
    printf "\nRe-running as 'root'... "
    exec su -c $0
fi

# color sheet
initializeANSI()
{
    esc=""
    
    blackf="${esc}[30m";    redf="${esc}[31m";    greenf="${esc}[32m"
    yellowf="${esc}[33m";    bluef="${esc}[34m";    purplef="${esc}[35m"
    cyanf="${esc}[36m";        whitef="${esc}[37m"
    
    blackb="${esc}[40m";    redb="${esc}[41m";    greenb="${esc}[42m"
    yellowb="${esc}[43m";    blueb="${esc}[44m";    purpleb="${esc}[45m"
    cyanb="${esc}[46m";        whiteb="${esc}[47m"
    
    reset="${esc}[0m"    # needed after any color is added to reset color, same as 'tput sgr0'
}

svn_apt()
{
    echo -e "Checking for a suitable SVN client . . ."; sleep 1
    dpkg --clear-avail >/dev/null 2>~/Error\ Log.txt
    if dpkg -l subversion >/dev/null 2>~/Error\ Log.txt; then
        echo -e "Dependencies met. Continuing on . . .\n"; sleep 1
    else
        echo -e "No suitable SVN package installed. Grabbing one now . . .\n"
        apt-get install -y subversion >/dev/null 2>~/Error\ Log.txt
    fi
}

svn_yum()
{
    echo -e "Checking for a suitable SVN client . . ."; sleep 1
    rpm -q subversion >/dev/null 2>~/Error\ Log.txt
    if [ "$?" != "0" ]
    then
        echo -e "No suitable SVN package installed. Grabbing one now . . .\n"
        yum -y install subversion >/dev/null 2>~/Error\ Log.txt
    else
        echo -e "Dependencies met. Continuing on . . .\n"; sleep 1
    fi
}

# menu functions
metasploit_apt()
{
    echo -e ${redf}"\n[Installing Metasploit]\n"${reset}; sleep 1
    echo -e "Checking out the latest version . . .\n"
    svn co https://www.metasploit.com/svn/framework3/trunk/ /pentest/metasploit >/dev/null 2>~/Error\ Log.txt
    echo -e "Installing dependencies for Metasploit . . .\n"
    apt-get install -y ruby rubygems >/dev/null 2>~/Error\ Log.txt
    echo -e "Metasploit installed . . .\n"
}

metasploit_yum()
{
    echo -e ${redf}"\n[Installing Metasploit]\n"${reset}; sleep 1
    echo -e "Checking out the latest version . . .\n"
    svn co https://www.metasploit.com/svn/framework3/trunk/ /pentest/metasploit >/dev/null 2>~/Error\ Log.txt
    echo -e "Installing dependencies for Metasploit . . .\n"
    yum -y install ruby rubygems >/dev/null 2>~/Error\ Log.txt
    echo -e "Metasploit installed . . .\n"
}

set_apt()
{
    echo -e ${redf}"\n[Installing Social-Engineer Toolkit]\n"${reset}; sleep 1
    echo -e "Checking out the latest version . . .\n"
    svn co http://svn.secmaniac.com/social_engineering_toolkit /pentest/set/ >/dev/null 2>~/Error\ Log.txt
    echo -e "Installing dependencies for S.E.T. . . .\n"
    chmod +x /pentest/set/./setup.py 
    /pentest/set/./setup.py install >/dev/null 2>~/Error\ Log.txt
    echo -e "S.E.T. installed . . .\n"
}

set_yum()
{
    echo -e ${redf}"\n[Installing Social-Engineer Toolkit]\n"${reset}; sleep 1
    echo -e "Checking out the latest version . . .\n"
    svn co http://svn.secmaniac.com/social_engineering_toolkit /pentest/set/ >/dev/null 2>~/Error\ Log.txt
    echo -e "Installing dependencies for S.E.T. . . .\n"
    yum -y install wget pexpect python-BeautifulSoup python-crypto python-openssl python-pefile >/dev/null 2>~/Error\ Log.txt
    echo -e "S.E.T. installed . . .\n"
}

aircrack_apt()
{
    echo -e ${redf}"\n[Installing Aircrack-ng]\n"${reset}; sleep 1
    echo -e "Checking out the latest version . . .\n"
    svn co http://trac.aircrack-ng.org/svn/trunk/ /pentest/aircrack-ng/ >/dev/null 2>~/Error\ Log.txt
    echo -e "Installing dependencies and building Aircrack-ng . . .\nAny errors will be logged in 'Error Log.txt' in the 'root' folder.\n"
    dpkg --clear-avail
    dpkg -l libssl-dev >/dev/null 2>~/Error\ Log.txt
    if [ "$?" != "0" ]; then
        apt-get install -y libssl-dev >/dev/null 2>~/Error\ Log.txt
    fi
    apt-get install -y build-essential >/dev/null 2>~/Error\ Log.txt
    cd /pentest/aircrack-ng
    make >/dev/null 2>~/Error\ Log.txt
    make install >/dev/null 2>~/Error\ Log.txt
    cd
    echo -e "Installing/Updating airodump-ng OUI file . . .\n"
    airodump-ng-oui-update >/dev/null 2>~/Error\ Log.txt
    echo -e "Aircrack-ng installed . . . \n"
}

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

# determine package manager?
echo -e "Searching for a familiar package manager . . ."; sleep 1
PKGMGR=
if command -v apt-get >/dev/null 2>~/Error\ Log.txt; then
    PKGMGR=apt
    echo -e "Found package manager 'APT' . . .\n"; sleep 1
elif command -v yum >/dev/null 2>~/Error\ Log.txt; then
    PKGMGR=yum
    echo -e "Found package manager 'YUM' . . .\n"; sleep 1
else
    echo -e "Could not determine a suitable package manager for the script.\nThis script is only for distros utilizing 'apt-get' or 'yum'.\nFeel free to edit the script to your needs if you know how.\n"
    exit
fi

svn_$PKGMGR

# menu start
while :
do
    cat << EOF
${greenf}H A X 0 R - T O O L - M E N U

1. Metasploit
2. Social-Engineer Toolkit
3. Aircrack-ng
4. Quit
EOF

echo -n -e "\nType a # and hit [ENTER]: "${reset}
read choice

case $choice in
    1) metasploit_$PKGMGR ;;
    2) set_$PKGMGR ;;
    3) aircrack_$PKGMGR ;;
    4) echo && exit ;;
    *) echo -e "\n\"$choice\" is not valid!\n"
esac
done

exit 0

```The "-h" option displays nicely. However, the "-v" option does not work. I don't get any syntax errors, but the script just continues as normal - pushing all output (except errors) into the dark hole of /dev/null. How would I go about setting it to actually display output? What am I missing here?

---

### Post by geirha on 2011-06-15
First off, getopts only handles short options; it'll handle -h and -v, but not --help or --verbose.

Secondly, your optstring "h:v" says that -h takes an argument. It doesn't make sense for -h to take an argument, and if you run your script with ```
./script -h -v
```  getopts will take -v as the argument to -h, and make it available in the special OPTARG variable, which your script ignores.

Now thirdly, if you do run your script with -v, all it does is set VERBOSE=1, but your script never uses that VERBOSE variable...

See [http://mywiki.wooledge.org/BashFAQ/035](http://mywiki.wooledge.org/BashFAQ/035) on how to handle long options as well.

---

### Post by GrantStoner on 2011-06-15
So I should so what? This?```
while getopts ":hv" OPTIONS ; do
``` And how would I go about adding verbosity then?

---

### Post by geirha on 2011-06-15
> **GrantStoner said:**
> So I should so what? This?```
while getopts ":hv" OPTIONS ; do
```

Yes, or getopts "hv", depending on whether you want error output from getopts or not.

> **GrantStoner said:**
> 

And how would I go about adding verbosity then?

That is entirely up to you. You have to decide what output should only be written when the -v option is used.

For example:
```

#!/bin/bash

usage() {
  echo Usage...
}

while getopts "hv" opt; do
  case $opt in
    h) usage; exit;;
    v) verbose=1;;
    \?) usage; exit 1;;
  esac
done

if ((verbose)); then
  echo "Searching for a familiar package manager..."
fi
# or
((verbose)) && echo "Searching for a familiar package manager..."

```

---

### Post by GrantStoner on 2011-06-15
So, I would have to rewrite all those parts of the script I want in verbose? There's nothing I can do to just have it display all the output? I was trying to avoid that... :/

---

### Post by geirha on 2011-06-15
Well, you could override the echo command I suppose
```

echo() { ((verbose)) && command echo "$@" || return 0; }

```

That won't do anything about the output of the other commands though.

---

