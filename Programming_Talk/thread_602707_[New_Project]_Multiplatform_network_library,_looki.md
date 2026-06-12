---
title: "[New Project] Multiplatform network library, looking for help"
date: 2007-11-04
forum: Programming Talk
---

### Post by tomcio on 2007-11-04
Hello!

**Features**
Few weeks ago i started working on a new network library, which will provide support TCP, UDP and SCTP protocols. Library should work on Linux, *BSD systems, Microsoft Windows and other. Library's code is designed to be as portable as it possible. 

I used C language. The main reason i that I know only this language ;) Moreover it's easy to make wrappers for other languages if library is in C.

I strongly used GLib facilities and GObject object system implementation.
[B]
Homepage
[/B][http://snllibrary.googlecode.com/](http://snllibrary.googlecode.com/)
[B]
Why I decided to create new library?
[/B]I was looking for a such library some time ago. I found GNet and libgnetwork. They weren't prefect. I want to have multiplatform library, with object system (GObject) and synchronous connections. 

**Current state**
Well, we can say, that I have a draft of library. So far I have working objects for TCP connections. I tested them only on Linux. I'm still working on it, please check SVN regularly.

[B]How can you help?
[/B]I don't want money, programming is my hobby, however I have some problems, here's a list:[LIST=1]
[*]I'm looking for someone, who can help me with porting library for Microsoft Windows. I almost now experience with programming for this system, I only know Winsock a bit.
[*]Someone, who knows SCTP will be helpful.
[*]I'm still a student and programming is only my hobby. It will be great if someone who is a **real** programmer will read my code and fix it. Any comments about what I'm doing wrong will helpful.
[*]Person who knows English better than me, and have some spare time to correct mistakes in documentation.
[*]If you have other idea and you want to help me, just send me an email![/LIST][B]Contact
[/B]tomcioj (at) gmail.com

---

### Post by aks44 on 2007-11-04
May I suggest that the dependency on glib is NOT a good idea for such a library?

---

### Post by tomcio on 2007-11-04
You didn't say why. 

GLib provides a lot of useful facilities, which make my work easier. Moreover it have quite clear API, to it shouldn't be a problem to learn it's basics.

GLib is multiplatform, that's another advantage.

The only thing, that I probably will change is public API. So far only object's API was supposed to be public, but now I think, that wrappers for POSIX functions (socket, recv, send, select, bind etc.) shold be available for end user too.

However if you give me good reasons I can change my mind, like I said I'm only a student. :)

---

### Post by aks44 on 2007-11-04
Of course it provides you, as the library developer, many facilities. But it's a PITA to users of your library.

KDE developers? Need to install GNOME dependencies, even though their project may otherwise be "pure" Qt. Same goes with other DEs & MS Windows. Talk about software bloat...

Notwithstanding the difficulty of building glib (thus your own lib) for the vast majority of Windows programmers.


Networking is very low level stuff, so it should depend on as few things as possible. Depending on something like glib for your own "commodity" is certainly not the way to go IMO when dealing with such core components as a networking lib. Just my $0.02...

---

### Post by tomcio on 2007-11-04
Ok, you (in my opinion) have partly right.

I checked, GLib depends only on glibc. Moreover Widows users doesn't need to compile GLib on their own, compiled libraries with all dependencies (not really wide, only libconv and getext) are available on GNOME ftp.

W need to go on some compromise, if SNL should be multiplatform.

---

### Post by _tomcio on 2008-08-16
Ok, I'll try to restore this topic.

Project is alive, I'm still working on it since lat year and - in my opinion - in next few months it may became quite stable and usable. So far I implement all my ideas, and checks how they work (I remove many, but some seems to be good, so they stay in the code).

**This is current status of a project:**

**From library developer's point of view:**
- library can be simply ported on other systems. Almost whole platform dependent code was isolated in one file
- rest of code is based on GLib/GObject, so it's fully portable (even Symbian OS provides GLib and GObject implementation)
- I really try to keep code clean and i add comments, to describe some specific code

**From application developer's point of view**
- whole public API is based on GLib/GObject, so it won't be a problem to make bindings for other languages e.g. Vala
- like above, API is based only on GObject and GLib, so developers, who knows GNOME environment will use my library after a while
- also library provides function for testing IP addresses (both IPv4 and IPv6), so you can check if given IP address i a loopback, private, multicast etc.
- library provides special type SnlAddress which represents both IP address and port number.
- now a bit about types, SNL provides such interfaces:
[list]SnlServer - implements common properties and signals
[list]SnlSyncServer - provides common synchronous methods
SnlAsyncServer - provides common asynchronous methods[/list][/list]
[list]SnlClient - implements common properties and signals
[list]SnlSyncClient - provides common synchronous methods
SnlAsyncClient - provides common asynchronous methods[/list][/list]
- and types:
[list]SnlTcpClient - this type represents TCP protocol based client
SnlTcpServer - this type represents TCP protocol based server[/list]

Note, that SnlTcpClient type implements SnlClient and both SnlSyncClient and SnlAsyncClient interfaces. It mean, that you can use bot async and sync methods on one client object. The same solution was used for SnlTcpServer.

**Download current code**
You can access project's subversion repository on it's homepage: [http://snllibrary.googlecode.com/](http://snllibrary.googlecode.com/) (tab "Source")

**Ok, now it's time for a wish list:**
1. Please look at this library's API and comment if it's good or not
2. If someone wants to contribute to project just send me an email (address above in first post)
3. Write what do you thing about project
4. If someone will be able to test library in future (when it will be stable) please contact me
5. I also look for people, who are able to prepare port for other systems like Microsoft Windows, Solaris etc.

---

