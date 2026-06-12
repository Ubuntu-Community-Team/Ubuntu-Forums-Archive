---
title: "Terminal- Bash question"
date: 2008-11-06
forum: Programming Talk
---

### Post by CTD12 on 2008-11-06
I need help on setting up the bash function in terminal.  I am very new to terminal and never have taken courses using terminal or any kind of command prompt... just looked on the internet to find command lines i need.  But what i need to know is how i can set up a text file to bash into with a command line that has multiple changes at the end of the command.
Example: i need to change my mac address at school so i can bypass the firewalls.  I have five or six mac addresses that the schools firewall accepts but sometime one works and other don't so i would like to set up a text file that has the command: sudo ifconfig en1 ether with the 5-6 addresses in a list under to choose from.  What i have to do right now is create 6 different txt files and bash into each one.  Is their a way to put all 6 mac addresses together so that i only have to bash one txt file and choose which mac address i would like to connect to the command?
thanks for any feedback sorry if confusing,
CTD12

---

### Post by pytheas22 on 2008-11-06
One way to do this would be to specify when you run the command which MAC address the script should use via an argument.  You can feed command-line arguments into a bash script using variables, where $1 represents the first argument, $2 the second, and so on.

I know that probably sounds very confusing, so let me just give you an example of what you would have to do.  I'll assume that you create a bash script called 'spoof-mac.sh'.  It should look something like:
```

#!/bin/bash

ifconfig eth0 hw ether $1
```

The '$1' in the script corresponds to the first argument that you give when you call the script in a terminal.  In other words, if you called the script by typing:
```

sudo spoof-mac.sh 012345678901
```

then the script would execute the following command:
```

ifconfig eth0 hw ether 012345678901
```

So using this method, you can easily use just one script to spoof any MAC of your choosing.

Let me know if this doesn't make sense or you need more clarification; I know these things are confusing if you've never programmed in bash.

Also, you'd find much more knowledgeable people if you posted this in the 'programming' section of the forum rather than the Apple one.

---

### Post by CTD12 on 2008-11-06
I need help on setting up the bash function in terminal. I am very new to terminal and never have taken courses using terminal or any kind of command prompt... just looked on the internet to find command lines i need. But what i need to know is how i can set up a text file to bash into with a command line that has multiple changes at the end of the command.
Example: i need to change my mac address at school so i can bypass the firewalls. I have five or six mac addresses that the schools firewall accepts but sometime one works and other don't so i would like to set up a text file that has the command: sudo ifconfig en1 ether with the 5-6 addresses in a list under to choose from. What i have to do right now is create 6 different txt files and bash into each one. Is their a way to put all 6 mac addresses together so that i only have to bash one txt file and choose which mac address i would like to connect to the command?
thanks for any feedback sorry if confusing,
CTD12

---

### Post by reality1011 on 2008-11-06
MAC addresses are hardware identification, normally unique to a computer...

IP addresses sounds like what you are trying to change..

Big difference

---

### Post by overdrank on 2008-11-06
Hi and the forum is not the place to ask to bypass restrictions at school. Thread closed.

---

### Post by bapoumba on 2008-11-07
> **CTD12 said:**
> ...
Example: i need to change my mac address at school so i can bypass the firewalls...
Circumventing local school rules will not be supported here, sorry. I'm closing the thread and will move it out from Apple sub-forum to General Help.

---

### Post by bapoumba on 2008-11-07
Good to see we are on the same page overdrank :)
Merged the other closed thread in this one.

---

