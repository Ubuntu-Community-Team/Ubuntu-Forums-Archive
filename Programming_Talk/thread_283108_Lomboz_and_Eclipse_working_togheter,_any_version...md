---
title: "Lomboz and Eclipse working togheter, any version..."
date: 2006-10-23
forum: Programming Talk
---

### Post by bitoiu on 2006-10-23
Hi mates,

Hi have the following problem.

I need to install the lomboz pluggin with eclipse. The thing is the repositoires version of eclipse works fine, and if I download 3.2 from the official site, and install in my home folder it works as well.

When I unzip the lomboz pluggin to one of those instalations, the cpu usage jumps to 100% and I simply can't work.

I've tried to set the memory to 512 when starting eclipse, but the problem is still there..

Has someone had the same problem or can help me with this?

Thanks.

---

### Post by FyreBrand on 2006-10-23
Make sure you have all of the required support packages installed (EMF, GEF, WTP, etc) with the required versions.

Next make sure you have a JDK installed and configured properly. A JRE won't work.  For this I would install Sun's JDK as opposed to the open source Java compilers because it looks like this was specifically built on this.  So until you get it running right I would try the option that should work and then experiment from there.

Here is a guide on installing and configuring Java: [**Java**]("https://help.ubuntu.com/community/Java")

An important thing to note in this case is the default JVM.  Ant and other applications sometimes use the first JVM in the list.  You might have to manually edit the list to make sure the SDK is at the top so it's used instead of some other JRE.  You will find the specifics on what I'm referring to under the section titled "Selecting the Default Java Version."

Good luck.

---

### Post by bitoiu on 2006-10-24
Hi,

First of all thanks for the anwser.

I have all that you said. I work with java for a quite long time, and only now i needed the lomboz pluggin. Every eclipse instalation works fine, but when I copy it lomboz to the pluggins the computer get to 100% cpu usage and never drops, making the work almost impossible.

When i don't have the lomboz pluggin the cpu is at 0%. My laptop is brand new so it's not a speed problem.

Thanks.

---

### Post by FyreBrand on 2006-10-24
Sorry I couldn't help.  I don't use eclipse a lot anymore.  I reinstalled it so I could try out the Aptana plug-in, but I'm getting a similar problem with it as you are getting with Lomboz.  I am also getting an error when the CDT plug-in loads.

I haven't been able to figure out what's wrong from the error log.  In my case there is an unhandled exception error with the eclipse UI and swt is being closed down too early.

---

### Post by bitoiu on 2006-10-29
The problem was simply this:

Lomboz really needs java 1.5 to work properly. I had both javas installed and used the 1.5 in the eclipse preferences, the thing is you need the default java in the machine to be 1.5. The solution I got was to set the PATH to the java 1.5 folder before all others, that way if u type java -version, it says 1.5. 

Then it works fine :D

---

