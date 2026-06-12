---
title: "I can't find/install the Arduino IDE software"
date: 2017-01-29
forum: New to Ubuntu
---

### Post by laptopdan on 2017-01-29
NewBie here, (LapTopDan)

  Just installed (L)ubuntu on an old Inspiron 6000.  Ran updates,  connected to email (IMAP), installed/tried/uninstalled  the a0d game.   (Successfully)

  I can't find/install the Arduino software.  I've downloaded the  tar.ball from the arduino website, but don't know how to install it...

  HELP, and be nice...


  Dan

---

### Post by deadflowr on 2017-01-29
Well, you could follow the guide here:
[https://www.arduino.cc/en/guide/linux]("https://www.arduino.cc/en/guide/linux")

or install the package from Ubuntu's repository archives
```
sudo apt-get install arduino
```
or if on Ubuntu 16.04  or newer:
```
sudo snap install arduino-mhall119
```
which is the newer snap package and will get updated more frequently.
But that's just my two cents.

---

### Post by laptopdan on 2017-01-29
Had issues, but fixed it and can see the IDE icon on the Desktop.

 ```
 arduino-1.8.1-linux64.tar.xz downloaded to /home/(username)/Downloads

  using a terminal of your choice          (I used Lubuntu's LXTerminal)
      "sudo mkdir /usr/share/Arduino"
      "sudo cp ./Downloads/arduino-1.8.1-linux64.tar.xz /usr/share/Arduino/arduino-1.8.1-linux64.tar.xz"
      "sudo chmod -R 777 /usr/share/Arduino"
      "sudo chown (username) /usr/share/Arduino"
      "sudo /usr/share/Arduino/arduino-1.8.1/install.sh"

 - - - -  ERROR  - - - -
Adding desktop shortcut, menu item and file associations for Arduino IDE...
touch: cannot touch '/home/(username)/.local/share/applications/mimeapps.list': No such file or directory
/usr/bin/xdg-mime: 807: 
/usr/bin/xdg-mime: cannot create /home/(username)/.local/share/applications/mimeapps.list.new: Directory nonexistent
 done!
- - - -  end ERROR  - - - -
      
      found missing directory / created the missing folder
      "sudo mkdir /home/(username)//local/share/applications"  
ran "sudo /usr/share/Arduino/arduino-1.8.1/install.sh"

- - - -  no ERROR  - - - -

Adding desktop shortcut, menu item and file associations for Arduino IDE... done!

- - - -  end no ERROR  - - - -

      "sudo chown (username)  /home/(username)//local/share/applications/*"

      The Desktop icon was associated with leafpad and wouldn't open...

      cd /home/(username)/Desktop
      "sudo chown dan arduino-arduinoide.desktop" #and my icon changed instantly
```
     

[http://www.pluggy.me.uk/arduino-ubuntu/](http://www.pluggy.me.uk/arduino-ubuntu/) shows additional software requirements that I'm installing before a reboot...

I'll update this soon...

---

### Post by wildmanne39 on 2017-01-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by laptopdan on 2017-01-29
Thanks wildmanne39 for the edit...

Still having issues...   The IDE gives me the option to execute or start in terminal, I see nothing when executing and the terminal flashes once and disappears.

I never had issues like this with XP, and yes there's a bigger learning curve with linux.  I've installed and configured wordpress on my pi, so I know that following directions should be easy, and I'm a stubborn little devil, so I'll keep trying till my eyes bleed...  I'm just stumped, so I'll get some sleep and retrace steps / research other options / and fingure this thing out...

---

### Post by laptopdan on 2017-01-29
SOLVED reloaded Lubuntu, installed additional software requirements following [http://www.pluggy.me.uk/arduino-ubuntu/](http://www.pluggy.me.uk/arduino-ubuntu/) directions.  Found the Arduino package that mysteriously appeared overnight, and I have the blinky sketch running on my UNOr3

---

