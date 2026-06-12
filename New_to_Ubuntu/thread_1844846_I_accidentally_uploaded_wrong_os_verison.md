---
title: "I accidentally uploaded wrong os verison"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Cubanicous on 2011-09-15
Does it make a difference if I have uploaded the 32 bit version on a computer that can support 64 bit os?

---

### Post by haqking on 2011-09-15
> **Cubanicous said:**
> Does it make a difference if I have uploaded the 32 bit version on a computer that can support 64 bit os?



Hi and welcome to the forums

It doesnt matter, if youn have more than 3GB (3.2 actually) of RAM then to utilise it you would need x64 version or PAE enabled 32 bit.

IF not then it dont really matter, where possible IMO it is best to install the x64 if hardware supports it, but no real biggie if you didnt.

peace

---

### Post by Cubanicous on 2011-09-15
Shoot. My laptop has 4gb of ram. So should I just reinstall ubuntu 64bit version then?

---

### Post by sarwiz on 2011-09-15
I don't know if it will make any difference. I kinda did the same thing in reverse. I downloaded and burned both 32 and 64 bit versions, and after loading Ubuntu onto my 32 bit laptop, and getting the dual boot with w7 working , etc, realized that I had used the 64 bit disc in it. And it is working just fine. Laptop is a 3 year old hp g60 (originally with vista installed) and only 2 gig ram. Hd has 9 partitions and has been running w7 and ubuntu9 for years. just recently had a windows crash, and reloaded everything.

---

### Post by Wim Sturkenboom on 2011-09-15
You can install the PAE kernel; it's in the repositories if I'm not mistaken. The 64 bit version however seems to be a lot faster according to tests on the phoronix website; if one however will notice the difference is another question ;)

---

### Post by kartabosh on 2011-09-15
the difference is noticeable, don't listen to that "it doesn't do anything unless you have more than 4gb of ram" rubbish.

few days ago i tested the 2 versions and the results showed great improvement (did i mention i have 3 gb of ram?)

32bit test 1
08:07:09 Begin test 
08:15:56 End test 
TOTAL: 8:47

32bit test 2
08:39:12 Begin test 
08:47:59 End test 
TOTAL: 8:47

32bit test 3
09:04:57 Begin test 
09:13:43 End test 
TOTAL: 8:46

64bit test 1
09:57:01 Begin test 
10:05:05 End test 
TOTAL: 8:04

64bit test 2
09:57:01 Begin test 
10:05:05 End test 
TOTAL: 8:04

64bit test 3
10:48:47 Begin test 
10:56:51 End test 
TOTAL: 8:04

here's the test if you want to try it out yourself

```
public class Test {

    static float percent = 1;
    static float endTest = Integer.MAX_VALUE;

    public static void printLog(String logMessage) {
        System.out.println(new java.text.SimpleDateFormat("hh:mm:ss '" + logMessage + 
                "'" ).format(java.util.Calendar.getInstance().getTime()));
    }

    public static void  main(String arg[]) {
    
    printLog("Begin test");
    
    for (int i = 0; i < endTest; i++){
        
        float[] variables = new float[100];
        
        variables[0] = i;
        
        for (int j = 1; j < variables.length; j++)
            variables[j] = variables[j-1];
        
        if (i > (float)endTest*((float)(percent/100)))
            printLog((int)percent++ + "%");
        
    }
    printLog("End test");
  }
    
}
```

---

### Post by -kg- on 2011-09-15
> **sarwiz said:**
> ...after loading Ubuntu onto my 32 bit laptop, and getting the dual boot with w7 working , etc, realized that I had used the 64 bit disc in it. And it is working just fine.

If you loaded the 64-bit version on your laptop, then it's not a 32-bit laptop.  A 64-bit OS will not install on a 32-bit computer.  In fact, you won't be able to run the Live- or other CD.  It will give you a message that you can't when you first try to boot to the CD/DVD.

---

### Post by RememberWhenItRained on 2011-09-16
> **Cubanicous said:**
> Does it make a difference if I have uploaded the 32 bit version on a computer that can support 64 bit os?

shouldn't but i'd go for a wipe and reinstall if your comp. can support it.

---

### Post by dfarrell07 on 2011-09-16
If you just installed, it would not be a big deal to wipe and install 64bit. I would do that, just to have the best possible option on your system. 

To be fair, you may never need all 4GB. To give you some perspective, I am running a C programming IDE, a VM of BackTrack5, seeding a bunch of random Linux distros, and have some other random stuff open like Skype, a terminal, PDFs, sound preferences, a few instances of GEdit, Chromium, file navigator, Dropbox, system monitor, and am getting updates from Twitter accounts via Gwibber every few minutes. I am using exactly 4GB of RAM. Screen shot attached.

---

### Post by Wim Sturkenboom on 2011-09-16
> **kartabosh said:**
> the difference is noticeable, don't listen to that "it doesn't do anything unless you have more than 4gb of ram crap"

few days ago i tested the 2 versions and the results showed great improvement (did i mention i have 3 gb of ram?)

Question is if the average user will really notice it in day to day use. How much faster will your emails be retrieved from the server or opened when you click on one? How much faster will a web page (e.g. ubuntuforums) be loaded and rendered?

I, for one, will probably not notice much difference except when I do image processing or possibly when ripping CDs. Others might benefit with complicated spreadsheet calculations or when creating videos. Or when compiling Ubuntu from its source code :lol:

---

### Post by haqking on 2011-09-16
> **kartabosh said:**
> **the difference is noticeable, don't listen to that "it doesn't do anything unless you have more than 4gb of ram rubbish**"

few days ago i tested the 2 versions and the results showed great improvement (did i mention i have 3 gb of ram?)




I never said it doesnt do anything, i said that it wont make any difference what one he uses as the OP sounded like he thought it was a mistake, so in that respect he can still run 32 bit just fine.
Also as for the 4GB, i said if he has more than 3.2GB of ram in his machine then to see it and use it he would need x64 or the PAE version.

Thankyou

---

### Post by kartabosh on 2011-09-17
> **haqking said:**
> I never said it doesnt do anything, i said that it wont make any difference what one he uses as the OP sounded like he thought it was a mistake, so in that respect he can still run 32 bit just fine.
Also as for the 4GB, i said if he has more than 3.2GB of ram in his machine then to see it and use it he would need x64 or the PAE version.

Thankyou

i wasn't targeting you, the 4gb ram thing a common misconception
my post wasn't some sort of reply to yours

---

### Post by haqking on 2011-09-17
> **kartabosh said:**
> i wasn't targeting you, the 4gb ram thing a common misconception
my post wasn't some sort of reply to yours

ok no worries ;-)

I wasnt offended, i was just clarifying incase

peace

---

### Post by kaldor on 2011-09-17
> **Cubanicous said:**
> Does it make a difference if I have uploaded the 32 bit version on a computer that can support 64 bit os?

It makes a difference, yes. But if you have 4 GB of RAM it will all be utilized. The benefit of 64bit is better performance. However, you probably won't notice the difference unless you do some intensive stuff.

---

