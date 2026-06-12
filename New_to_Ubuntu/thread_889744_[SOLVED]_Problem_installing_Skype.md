---
title: "[SOLVED] Problem installing Skype"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by wintersnows on 2008-08-14
hiya, could someone could help me to solve this problem? 

I was trying to install skype on Ubuntu, followed by the command given at: [http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/](http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/) and then I typed in the following but it doesn't work at all.:
 
sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo aptitude install skype

Then, the problem comes when I tried another way by downloaded a skype.deb file and tried to open with GDebi Package installation. It prompts out "Software index is broken" and it says [This is a major failure of your software management system. Please check for broken packages with synaptic. check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.] Then, I tried to do as mentioned in the terminal but the terminal doesn't allows me to run/get any of this commands e.g.:

sudo apt-get install skype
sudo apt-get update or even
sudo apt-get python 2.5

and etc apt-get. It appears the errors in the terminal as:

E: Type ‘--15:59:08--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

Could you show me how to fix the problem and install skype on Ubuntu? 

Thank you very much!

---

### Post by hyper_ch on 2008-08-14
well, what does the error message say?

---

### Post by sayakb on 2008-08-14
Which Ubuntu version are you using (Feisty - 7.04?)
At a terminal, do:
```
sudo apt-get install -f
```
If you have 8.04, then add the medibuntu repos following this: [http://ubuntuforums.org/showthread.php?t=713009](http://ubuntuforums.org/showthread.php?t=713009)
Then do:
```
sudo apt-get install skype
```

---

### Post by wintersnows on 2008-08-14
The errors message said when I typed any of the sudo apt-get install and it turns up the errors as the following:: 

E: Type ‘--15:59:08--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

I think most probably I have typed in the unwork code as this:
sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo aptitude install skype

and I am not using Feisty - 7.04. I am using Ubuntu 8.04 or checked at About GNOME, the version: 2.22.3 thanks.

---

### Post by hyper_ch on 2008-08-14
I know what the error says.. but do you actually read and comprehend it?

---

### Post by wintersnows on 2008-08-14
I tried with whatever sudo apt-get install ... 

it replies me the same errors message. Is it I need to sort out the wrong typed stuff or get into Synaptic to sort it? COuld someone help? Thank you

---

### Post by nothingspecial on 2008-08-14
> **wintersnows said:**
> The errors message said when I typed any of the sudo apt-get install and it turns up the errors as the following:: 

E: Type &#8216;--15:59:08--&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

I think most probably I have typed in the unwork code as this:
sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo aptitude install skype

and I am not using Feisty - 7.04. I am using Ubuntu 8.04 or checked at About GNOME, the version: 2.22.3 thanks.

You need to remove the feisty medibuntu line from your sources list and add the Hardy one.

---

### Post by wintersnows on 2008-08-14
I am new in Ubuntu. I suspect I have typed the wrong command stuff as I am not using the fesital 7 version. Please show me.

---

### Post by wintersnows on 2008-08-14
can you show me the command of remove the feistal and add the hardy one? thanks a lot

---

### Post by nothingspecial on 2008-08-14
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```



```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by nothingspecial on 2008-08-14
That will add the hardy one.

To remove the feisty one go to system > administration > software sources.
click on the feisty medibuntu line and click remove or delete or whatever it says.

---

### Post by wintersnows on 2008-08-14
yes. Thanks you *Phew*.. . Both of your code works. Is this means I have remove the feistal 7 by adding the Hardy one?

should I write now:

sudo apt-get install skype ???

Thank you

---

### Post by nothingspecial on 2008-08-14
Look at this thread again, i put how to remove the feisty one in another post

---

### Post by cosine352 on 2008-08-14
OR download the .deb here

> [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

---

### Post by wintersnows on 2008-08-14
yes, I am on Software Sources but I can't find the Feistal. Where about the TAB? I don't found it on Third-Party software, it's all written Hardy.

---

### Post by wintersnows on 2008-08-14
yes. I downloaded a skype.deb version

---

### Post by nothingspecial on 2008-08-14
> **wintersnows said:**
> yes, I am on Software Sources but I can't find the Feistal. Where about the TAB? I don't found it on Third-Party software, it's all written Hardy.

Maybe it gets removed when you add the Hardy one

---

### Post by wintersnows on 2008-08-14
wow.. great! I have downloaded the skype .deb and now tried to open with GDebi Package Installer again. It appears another new prompt 
"Broken dependencies" [Your system has broken dependencies. This application can not continue until this is fixed. To fix it run 'sudo synaptic' or 'sudo apt-get install =f' in a terminal window. ] What should I do?

---

### Post by nothingspecial on 2008-08-14
Run those commands in a terminal.

---

### Post by wintersnows on 2008-08-14
Thanks a lot Nothing Special!! It works and I get my skype done. However, I need to configure another stuff for my assessment: Courier-IMAP in order for my program to use it to test and run the results. Could you shows me details/ideas? 

Thanks again!

---

### Post by nothingspecial on 2008-08-14
> **wintersnows said:**
> Courier-IMAP in order for my program to use it to test and run the results. Could you shows me details/ideas? 

I`m sorry buddy I don`t know anything about those. 

You need to mark this thread as solved, and then start a new thread called "Help with Courier-Imap" or something like that or some one who does know about that stuff wont see it `cause the question is in a thread about skype.

Glad you got it sorted though :guitar:

---

### Post by wintersnows on 2008-08-14
Thanks so much to Nothing special. Where to click "solve" ?

---

### Post by nothingspecial on 2008-08-14
Click thread tools at the top of the page here -

[ATTACH]81556[/ATTACH]

At the bottom of the list will be an option to Mark this tread as solved.

---

