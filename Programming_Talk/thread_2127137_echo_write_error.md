---
title: "echo write error?"
date: 2013-03-19
forum: Programming Talk
---

### Post by kaspar_silas on 2013-03-19
Quick question.

I am running Ubuntu 12.04 in a Virtualbox and have shared a host folder with it.
This auto mounts at /media/sf_Transfer
If I try to echo to a new file on the shared folder all is fine :

$ echo "AAA" >> AnewFile
$ cat AnewFile
AAA

However if I now try to append to this new file it fails:

$ echo "AAA" >> AnewFile
bash: echo: write error: Protocol error

It's not just bash as I can do the equivalent in any other language, eg in C++ :

```
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    const char fileName[]="/media/sf_Transfer/AnewFile";
    ofstream temp(fileName, ios::app);
    if( temp<<"AAA"<<endl ) cout<<"Success"<<endl;
    else cout<<"Failure"<<endl;
    temp.close();
    return 0;
}

```

and still get the same odd result that it works if the file doesn't exist otherwise it fails.

If I append "by-hand" ie with a text editor (nano/gedit/vi) all is fine. Any ideas?

---

### Post by kaspar_silas on 2013-03-20
Okay so just to "help" anyone else who runs into the same issue. This seems to be a virtual box shared folders thing. Whatever way the folder is being shared you can create and delete files you don't seem to be able to edit them or even change the permissions.

For example:
$ ls -l /media/sf_Transfer/AAA
-rwxrwx--- 1 root vboxsf 4 Mar 19 11:09 /media/sf_Transfer/AAA
$ sudo chmod 777 /media/sf_Transfer/AAA
[sudo] password for kaspar:
$ ls -l /media/sf_Transfer/AAA
-rwxrwx--- 1 root vboxsf 4 Mar 19 11:09 /media/sf_Transfer/AAA

I am guessing text editors work as they rewrite the whole file when writing.

---

### Post by iMac71 on 2013-03-20
you might try to use chown instead of chmod```
sudo chown kaspar:kaspar /media/sf_Transfer/AAA
```

---

### Post by kaspar_silas on 2013-03-21
Cheers for the suggestion but it's the same result. The command runs okay but the owner and group is not changed :

[as root]
$ chown kaspar:kaspar /media/sf_Transfer/AAC && echo "Success"
Success
$ ls -l /media/sf_Transfer/AAC 
-rwxrwx--- 1 root vboxsf 3 Mar 21 09:33 /media/sf_Transfer/AAC

---

### Post by iMac71 on 2013-03-21
> **kaspar_silas said:**
> Cheers for the suggestion but it's the same result. The command runs okay but the owner and group is not changed :

[as root]
$ chown kaspar:kaspar /media/sf_Transfer/AAC && echo "Success"
Success
$ ls -l /media/sf_Transfer/AAC 
-rwxrwx--- 1 root vboxsf 3 Mar 21 09:33 /media/sf_Transfer/AACwhen you write [as root] do you mean this:```
sudo su
chown kaspar:kaspar /media/sf_Transfer/AAC
```or what else?

---

### Post by kaspar_silas on 2013-03-21
Yeah using "su" although actually my user is a member of vboxsf so I shouldn't actually need root permissions anyway.

---

### Post by steeldriver on 2013-03-21
What's the underlying host filesystem? here's what I get in a Mint VM on Windows 7

```

steeldriver@mint-vm ~/Desktop $ touch /media/sf_Documents/file
steeldriver@mint-vm ~/Desktop $ echo "something" > /media/sf_Documents/file
steeldriver@mint-vm ~/Desktop $ echo "something else" >> /media/sf_Documents/file
steeldriver@mint-vm ~/Desktop $ echo "something even more" >> /media/sf_Documents/file
steeldriver@mint-vm ~/Desktop $ cat /media/sf_Documents/file 
something
something else
something even more
steeldriver@mint-vm ~/Desktop $

```

OTOH 'chmod 777' doesn't work - but I suspect that may just be because the underlying (NTFS) filesystem can't handle the UNIX permission bits:

```

steeldriver@mint-vm ~/Desktop $ ls -l /media/sf_Documents/file 
-rwxrwx--- 1 root vboxsf 25 Mar 21 20:32 /media/sf_Documents/file
steeldriver@mint-vm ~/Desktop $ 
steeldriver@mint-vm ~/Desktop $ chmod 777 /media/sf_Documents/file 
steeldriver@mint-vm ~/Desktop $ ls -l /media/sf_Documents/file
-rwxrwx--- 1 root vboxsf 45 Mar 21 20:34 /media/sf_Documents/file

```

---

### Post by kaspar_silas on 2013-03-22
I am using Windows 7 as the host and Ubuntu 12.04 as the client. I think it used to work so the only thing I can guess happened is that I updated virtual box and this introduced this bug. (I am on VirtualBox 4.2.8)

It's pretty consistent. In just about every language I know I can delete,read and make files just not edit them.  

O and yeah I guess the same for the changing permissions bit.

---

