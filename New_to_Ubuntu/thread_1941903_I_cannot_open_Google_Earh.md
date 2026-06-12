---
title: "I cannot open Google Earh"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by User Anna on 2012-03-16
Hi everyone! :)
I have ubuntu 10.04.1 32-bit.
I installed Google Earth 6 ubuntu 32-bit deb.
When I click on "Google Earth", it doesn`t open.
I did in terminal:
sudo apt-get install lsb

and then

$ sudo apt-get update
$ sudo apt-get install lsb-core

It didn`t help.
Can u help me, please?

Thank you.

---

### Post by winh8r on 2012-03-16
Did you follow these instructions:

[http://tinyurl.com/7jd3ahd]("http://tinyurl.com/7jd3ahd")


Check them over and look at the troubleshooting section too.

---

### Post by yetiman64 on 2012-03-16
Hi User Anna, could you please open a terminal window (Applications > Accessories > Terminal) and copy and paste in the code below and press enter,

```
google-earth
```This would normally launch google earth, but in this case may very well display errors. This should help in narrowing down what the problem is.

If it does give errors copy them from the terminal window (drag a selection over them, right click and select copy) and then paste them back here in your editor window between code tags eg. [noparse]```
<your pasted output>
```[/noparse]. The simplest way of doing this is to highlight the output and then click on the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar.

---

### Post by User Anna on 2012-03-16
```
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/anna/.googleearth/crashlogs/crashlog-4f637472.txt

```

---

### Post by yetiman64 on 2012-03-16
I just googled the google-earth error you got (rather ironic ;)).

Could you please open the crashlog with (in terminal again),

```
gedit /home/anna/.googleearth/crashlogs/crashlog-4f637472.txt
```and copy the contents in gedit and paste here just like you did for the first lot of output. 

There should be some info in there that describes your system. One person on google groups found by disabling the ruler helped him, but I think it will be system dependent, could be other faults that can cause this. If nothing obvious shows in the crashlog output, the matter may need to be reported directly to google. Not sure how you would go about that, I've never had to deal with them for any problems like this.

---

