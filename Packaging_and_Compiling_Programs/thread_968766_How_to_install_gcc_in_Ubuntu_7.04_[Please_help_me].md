---
title: "How to install gcc in Ubuntu 7.04 [Please help me]"
date: 2008-11-02
forum: Packaging and Compiling Programs
---

### Post by Jayadheer on 2008-11-02
Hello all,
          This is the first time I am posting a thread in Ubuntu forum and I am very new to Ubuntu. 

     I have installed Ubuntu 7.04 in my PC and when try to compile my first C program I got error message like this 

-- error - stdio.h no such file or directory.

I have realised that I don't have gcc compiler installed. 
-- >apt-get install gcc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.





I have used fedora and suse Linux before, I did get any such problems.


Can any one please help me with this. How to fix it.


Thanks in advance

---

### Post by ad_267 on 2008-11-02
Install the build-essential package.

Also, you might want to consider updating to 8.10 or 8.04.

---

### Post by kostkon on 2008-11-02
> **Jayadheer said:**
> Hello all,
          This is the first time I am posting a thread in Ubuntu forum and I am very new to Ubuntu. 

     I have installed Ubuntu 7.04 in my PC and when try to compile my first C program I got error message like this 

-- error - stdio.h no such file or directory.

I have realised that I don't have gcc compiler installed. 
-- >apt-get install gcc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.





I have used fedora and suse Linux before, I did get any such problems.


Can any one please help me with this. How to fix it.


Thanks in advance
You will need to install the [*build-essential*]("http://packages.ubuntu.com/feisty/build-essential") package. It will give you the libc6 libraries that you need.

---

### Post by Jayadheer on 2008-11-03
Thanks for help just now I have installed gcc and g++.

 my gcc is working fine. Now my problem is with g++

when I try to compile the basic c++ program typed like this in vim editor



include<iostream>
using namespace std;
int main()
{
 cout << "Hello";
 return 0;
}

 I got follwing errors when I try with this command


  >g++ 1.cpp

1.cpp:1: error: expected constructor, destructor, or type conversion before &#8216;<&#8217; token
1.cpp: In function &#8216;int main()&#8217;:
1.cpp:5: error: &#8216;cout&#8217; was not declared in this scope

---

### Post by ad_267 on 2008-11-03
You're missing a "#" in front of your include.

---

### Post by Jayadheer on 2008-11-03
> **ad_267 said:**
> You're missing a "#" in front of your include.

Thanks I did't observe it. I thought one of library may be missing 

Thanks alot

---

