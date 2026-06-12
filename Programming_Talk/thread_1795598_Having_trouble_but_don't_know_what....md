---
title: "Having trouble but don't know what..."
date: 2011-07-02
forum: Programming Talk
---

### Post by slashwannabe94 on 2011-07-02
Hello all, I'll try and keep this quick and short. 

I've written a script to install and configure logkeys but their is a piece of code that won't work for some reason. It's the case function that i can't figure out. Here is my code. 

```
#!/bin/bash
# # This script installs and configures logkeys on static-static-desktop
# Check if root

if [ "$(/usr/bin/id -u)" != "0" ]; then
   exec /usr/bin/sudo "$0"
else
   echo "Elevated priviledges..."
fi

#Define the function logfunct
logfunct()
{   
   echo "Satisfying dependencies..."
   apt-get install build-essential
   [[ $? -eq 0 ]] || { echo "Failed to install build-essential, exiting..."; exit 1; }
   echo "Downloading logkeys from source... Please wait: "
   mkdir $HOME/Keylogger; cd $HOME/Keylogger
   wget http://logkeys.googlecode.com/svn/wiki/keymaps/en_GB.map
   echo "Downloaded en_GB.map "
   wget http://logkeys.googlecode.com/files/logkeys-0.1.1a.tar.gz
   [[ $? -eq 0 ]] || { echo "Failed to download logkeys from source, exiting..."; exit 1; }
   echo "Decompressing the archive..."
   tar -xf logkeys-0.1.1a.tar.gz
   cd logkeys-0.1.1a
   echo "Building package..."
   ./configure
   make
   make install
   [[ $? -eq 0 ]] || { echo "Failed to install logkeys, exiting..."; exit 1; }
 }   

if [ -f /usr/local/bin/logkeys ]; then
   echo "Logkeys is installed..."
else
   logfunct   
fi  

[COLOR=Red]# Define the function bootfunct
bootfunct()
{
   cd ~
   echo "Creating a backup of the /etc/init.d/rc.local file..."
   [[ -e /etc/init.d/rc.local ]] && cp /etc/init.d/rc{.local,.bak}
   echo "Adding the code to the /etc/init.d/rc.local file..."
   cat <<'EOF' >> /etc/init.d/rc.local
/usr/local/bin/logkeys -s -m $HOME/Keylogger/en_GB.map -o $HOME/Keylogger/.loggy.log
EOF
}

clear[/COLOR] [COLOR=Red]
echo "1=Yes"
echo "2=No"
echo -n "Would you like to start the Keylogging session on boot: "   
read choice1
case $choice1 in
   1) bootfunct
      ;;
   2) echo "2 selected, exiting now..."
      exit
      ;;
   *) echo "Invalid option selected bootfunct failed, exiting..."
esac[/COLOR]

clear
echo "1=Yes"
echo "2=no"
echo -n "Would you like to start a Keylogging session now: "

read choice
case $choice in
   1) sudo logkeys -s -m $HOME/Keylogger/en_GB.map -o $HOME/Keylogger/.loggy.log
      echo "Logging session started, to view the log look in the Keylogger directory..."
      ;;
   2) echo "2 selected, exiting now..."
      ;;
   *) echo "Invalid option selected, exiting now..."
esac
 
exit

```When i run this this script everything works but the bootfunct function... Can anyone help me with this, as i can't see what i'm doing wrong. I have highlighted in red what i think might be wrong but i can't really pin it on anything. 

Thanks people, 
SlashWannabe94

---

