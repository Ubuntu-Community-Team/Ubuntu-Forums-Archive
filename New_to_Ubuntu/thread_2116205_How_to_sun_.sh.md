---
title: "How to sun .sh"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by JohanDuPlessis on 2013-02-15
I have downloaded a utility Apk2Gold that will only work with Linux so I downloaded and installed Ubuntu in dual boot with Windows 7.  I copied the Apk2Gold to my Home folder and also installed git, python and mercurial...they are required.
 
The instructions then required a script make.sh to install apk2gold..so I went to its properties, made it executabl and then double-clicked it to run.
 
The next procedure is to run the apk2gold by typing apk2gold <target>.apk in this case a memo.apk I wish to decompile.  Ubuntu does not find the command apk2gold.  Can someone help. I do not know where this file is installed and cannot find it.  I am an absolute nooby with Ubuntu

---

### Post by schragge on 2013-02-15
I guess the program has been installed in your home directory.

Open the terminal (Ctrl+Alt+T), and execute this
```

find ~ -type f -name apk2gold

```
Then post the output here

---

### Post by JohanDuPlessis on 2013-02-15
yes it finds the file but the one that came with apk2gold
 
When I type ***apk2gold memo.apk*** in the terminal all I get is **command not found**

---

### Post by omeomi on 2013-02-15
> **JohanDuPlessis said:**
> When I type ***apk2gold memo.apk*** in the terminal all I get is **command not found**

That's because this only works if you have a binary for this program in one of the bin folders (/usr/bin etc.).

If you know the path to the program (using schragge's command) you can run it by either going to that folder or typing this:
```
$ /path/to/file/apk2gold memo.apk
```

Also, if this program is a shell script (e.g. it is called apk2gold**.sh**) you need to preped 'sh' before this command:
```
$ sh /path/to/file/apk2gold.sh memo.apk
```

In both cases you ofcourse need to replace /path/to/file with the actual path.

---

### Post by Nr90 on 2013-02-15
Try this:
Put the apk in the directory where the apk2gold file is.
Open a terminal and move to the apk2gold directory.
Type: ./apk2gold memo.apk

---

### Post by schragge on 2013-02-15
There is no other *apk2gold*, but the one that comes with the package. *make.sh* doesn't install anything in system folders. To run the script from terminal you should either specify the path to it, or put it into one of the directories referenced by $PATH.

If you've unpacked it in *apk2gold-master/* then launch it with
```

apt2gold-master/apk2gold [color=green]memo.apk[/color]

```
or try this
```

`find ~ -type f -name apk2gold` memo.apk

```

---

### Post by JohanDuPlessis on 2013-02-15
Yes - I did unpack the apk2gold-master into its own directory and i did paste the memo.apk file there also....I then opened a terminal window changed directory to where apk2gold-master is and executed apk2gold memo.apk...
 
All I get is apk2gold: command not found..???
 
Has it got something to do with a missing binary file?
 
Sorry but my exposure to ubuntu is less than a day

---

### Post by schragge on 2013-02-15
If you are in the apk2gold-master folder already then do
```
./apk2gold memo.apk
``` like **Nr90** suggested. Do not forget [highlight]./[/highlight]

---

### Post by JohanDuPlessis on 2013-02-15
Ok - Now I have it! When I use the command $ sh apk2gold Memo.apk then it works..Thanks everyone for good and quick response

---

