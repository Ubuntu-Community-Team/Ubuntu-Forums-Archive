---
title: "New Android Project Build"
date: 2011-07-20
forum: Programming Talk
---

### Post by NoFriends on 2011-07-20
Hi,

I'm following the Hello World Android Tutorial and having some issue.

I've followed steps on the android developers webpage and now at the point of creating my first test project.

On the NEW ANDROID PROJECT page,

Filled out the details and the error I am getting is the below:

An SDK Target must be specified.

Because of this i am not able to click Next and proceed.

All help appreciated.

---

### Post by SevenMachines on 2011-07-20
Are there no build target listed below that? If not, you need to install one or more sdk platforms. Go to
windows->android sdk
and look at available packages, you should have a bunch of the type
'SDK Platform Android etc'

---

### Post by NoFriends on 2011-07-20
> **SevenMachines said:**
> Are there no build target listed below that? If not, you need to install one or more sdk platforms. Go to
windows->android sdk
and look at available packages, you should have a bunch of the type
'SDK Platform Android etc'


Hi,

Thanks for your response, I have already installed one or more platforms.

Latest & Version 2.3 to be exact.

So I'm not to sure if this is caused by something I may have missed earlier ?
and correct,There are no Build Targets listed, All Greyed out.

I installed the starter package to my Desktop and i went into Eclipse, 
click Window, Preference and set it to be     home/user/Desktop/android-sdk-linux_x86

Is this correct ?

---

### Post by SevenMachines on 2011-07-20
Hmm...
When you go to window->preferences->android do you have
the correct sdk location and a list of installed platforms underneath?
Do you have a list of platforms in 
```
 $ls ~/Desktop/android-sdk-linux_x86/platforms
```

---

### Post by NoFriends on 2011-07-20
Sorry for late reply, Working on it while keeping an eye here, 

yes, using that command i have the following:

android-10  android-12  android-3  android-7
android-11  android-13  android-4  android-8

it seems as though, only when i added the latest version, nothing showed.

But now i have installed all the versions for the complete package they have all shown.

---

### Post by doas777 on 2011-07-20
> **NoFriends said:**
> Hi,

I'm following the Hello World Android Tutorial and having some issue.

I've followed steps on the android developers webpage and now at the point of creating my first test project.

On the NEW ANDROID PROJECT page,

Filled out the details and the error I am getting is the below:

An SDK Target must be specified.

Because of this i am not able to click Next and proceed.

All help appreciated.


if i understand what you are saying, then you need to tick the box next to one of the SDK versions in the New Project dialog.

---

### Post by NoFriends on 2011-07-20
Thanks for your response doas777.

I originally did download and install the latest version, but it did not seem to refresh and update eclipse when i attempted to create a project, but now that i have downloaded them all, eclipse has updated and i am now in process of playing about with the new project.

No doubt in the close future i will be posting for some help and advice again.

Thanks to all for your help.

---

