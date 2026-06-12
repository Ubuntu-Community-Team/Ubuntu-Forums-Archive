---
title: "Bash Script Issues (Help?)"
date: 2011-06-15
forum: Programming Talk
---

### Post by GrantStoner on 2011-06-15
Okay. So long story short, I was writing a script on Ubuntu, and couldn't get it to work properly (installing Metasploit). So I switched to Fedora for a while and re-wrote the script. Needless to say - it worked flawlessly. But I ended up coming back to Ubuntu because I can't stand how long YUM takes! Re-wrote the script AGAIN, this time to work on Fedora AND Ubuntu (so I don't have to rewrite it if I ever switch again). In rewriting the script from scratch - installing Metasploit and S.E.T. work fine in Ubuntu and Fedora. However, when I try to install Fast-Track, the script hangs at "Installing dependencies for Fast-Track..." Installing S.E.T. and Fast-Track should be identical instructions. So can anyone see why it's not working?
```

#! /bin/bash

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
    svn co http://svn.secmaniac.com/social_engineering_toolkit /pentest/set/ >/dev/null
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

fasttrack_apt()
{
    echo -e ${redf}"\n[Installing Fast-Track]\n"${reset}; sleep 1
    echo -e "Checking out the latest version . . .\n"
    svn co http://svn.secmaniac.com/fasttrack /pentest/fasttrack >/dev/null 2>~/Error\ Log.txt
    echo -e "Installing dependencies for Fast-Track . . .\n"
    chmod +x /pentest/fasttrack/./setup.py
    /pentest/fasttrack/./setup.py install >/dev/null 2>~/Error\ Log.txt
    echo -e "Fast-Track installed . . .\n"
}

clear

if [ "$UID" != "0" ]; then
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

# determine package manager?
echo -e "Searching for a familiar package manager . . ."; sleep 3
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

svn_$PKGMGR

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
    1) metasploit_$PKGMGR ;;
    2) set_$PKGMGR ;;
    3) fasttrack_$PKGMGR ;;
    4) aircrack-ng_$PKGMGR ;;
    5) echo && exit ;;
    *) echo -e "\n\"$choice\" is not valid!\n"
esac
done

exit 0

```

---

