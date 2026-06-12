---
title: "How do I install OpenAL for C++"
date: 2013-03-01
forum: Programming Talk
---

### Post by ProvenDantheman on 2013-03-01
I would like to develope with OpenAL, but I can't seem to get the packages.

---

### Post by Zugzwang on 2013-03-02
> **ProvenDantheman said:**
> I would like to develope with OpenAL, but I can't seem to get the packages.

It would be helpful if you could elaborate. Can't you find the package, can't you download it, or does installation fail? In the latter case, I would suggest that you copy&paste the precise error messages here in order to get help.

---

### Post by ProvenDantheman on 2013-03-02
> **Zugzwang said:**
> It would be helpful if you could elaborate. Can't you find the package, can't you download it, or does installation fail? In the latter case, I would suggest that you copy&paste the precise error messages here in order to get help.

I go to OpenAL's website, connect.creativelabs.com/**openal**/, but I can't find any of the packages for linux.

---

### Post by ProvenDantheman on 2013-03-02
Never mind, I just found it somewhere else :)

---

### Post by Mr. Shannon on 2013-03-02
> **ProvenDantheman said:**
> I go to OpenAL's website, connect.creativelabs.com/**openal**/, but I can't find any of the packages for linux.

You should install OpenAL with the package manager unless you have a specific reason for needing a different version.  Installing any other way could potentially break software on your system that relies upon OpenAL.  The normal way to install the developer packages for OpenAL is:
```
sudo apt-get install libopenal-dev
```

---

### Post by keghn on 2013-04-18
[URL="http://connect.creativelabs.com/openal/Downloads/Forms/AllItems.aspx?RootFolder=%2fopenal%2fDownloads%2fALUT&FolderCTID=&View=%7b6A9700C6-7248-4CD2-83F5-268F2C176072%7d"]
sudo apt-get install libalut-dev
sudo apt-get install libopenal-dev

 [/URL]go to: 

[http://connect.creativelabs.com/openal/Downloads/Forms/AllItems.aspx?RootFolder=%2fopenal%2fDownloads%2fALUT&FolderCTID=&View=%7b6A9700C6-7248-4CD2-83F5-268F2C176072%7d](http://connect.creativelabs.com/openal/Downloads/Forms/AllItems.aspx?RootFolder=%2fopenal%2fDownloads%2fALUT&FolderCTID=&View=%7b6A9700C6-7248-4CD2-83F5-268F2C176072%7d)

 and down load: 

freealut-1.1.0.tar


compile with: 


g++ test.cpp -lalut -lopenal -o test 


		or 


gcc helloworld.c -lalut -lopenal -o helloworld

---

