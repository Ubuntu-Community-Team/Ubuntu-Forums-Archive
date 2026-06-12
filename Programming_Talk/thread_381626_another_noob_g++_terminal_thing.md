---
title: "another noob g++ terminal thing"
date: 2007-03-11
forum: Programming Talk
---

### Post by mills on 2007-03-11
hi ya 

trying to learn programming with c++ and i want to learn with the terminal 
becuase that seems to be the way to go but i cant compile from terminal

i've tried
```
g++ -o hello hello.cpp
g++ -g -Wall -o hello hello.cpp
```

but i get these errors

hello.cpp:11: error: stray ‘\302’ in program
hello.cpp:11: error: stray ‘\240’ in program
hello.cpp:11: error: stray ‘\302’ in program
hello.cpp:11: error: stray ‘\240’ in program
hello.cpp:11: error: stray ‘\302’ in program
hello.cpp:11: error: stray ‘\240’ in program
hello.cpp:11: error: stray ‘\302’ in program
hello.cpp:11: error: stray ‘\240’ in program
hello.cpp:11: error: stray ‘\302’ in program
hello.cpp:11: error: stray ‘\240’ in program
hello.cpp:12: error: stray ‘\302’ in program
hello.cpp:12: error: stray ‘\240’ in program
hello.cpp:12: error: stray ‘\302’ in program
hello.cpp:12: error: stray ‘\240’ in program
hello.cpp:12: error: stray ‘\302’ in program
hello.cpp:12: error: stray ‘\240’ in program
hello.cpp:12: error: stray ‘\302’ in program
hello.cpp:12: error: stray ‘\240’ in program
hello.cpp:12: error: stray ‘\302’ in program
hello.cpp:12: error: stray ‘\240’ in program

iam really not sure whats going wrong, ive installed build essential and 
looked through the forums and g++ man pages 
iam sure its something simple, 

any ideas?

ps. when i double click on the file in my home folder it opens a terminal as root, is that normal? safe?

---

### Post by po0f on 2007-03-11
mills,

You didn't happen to transfer 'hello.cpp ' from a Windows box, did you?

---

### Post by mills on 2007-03-11
i created the code in gedit, saved it in my homefolder

then tried the above code in terminal

iam new to linux, so not sure what you mean by windows box

if you mean my microsoft windows xp partition then no i didnt

just copied and pasted from an ebook

// ask for a person's name, and greet the person

#include <iostream>

#include <string>



```
int main()

{

    // ask for the person's name

    std::cout << "Please enter your first name: ";



    // read the name

    std::string name;         // define name

    std::cin >> name;         // read into



    // write a greeting

    std::cout << "Hello, " << name << "!" << std::endl;

    return 0;

}
```

maybe the codes supposed to be modified for linux???

---

### Post by Darkness3477 on 2007-03-11
Well, I edit the above code slightly to this (mostly because I think it's more readable

So, this is what I have now
```
#include <iostream>
#include <string>

int main()
{
using namespace std; //Get's rid of the need to put std::cout and all that

    // ask for the person's name

    cout << "Please enter your first name: ";



    // read the name

    string name;         // define name

   cin >> name;         // read into



    // write a greeting

    cout << "Hello, " << name << "!" << endl;

    return 0;

}
```

I then ran the program using

```
 g++ -o help -g -Wall help.cpp

```

So, I'll ask the question that everyone seems to... Have you download the build-essential?

---

### Post by lnostdal on 2007-03-11
stray characters mean illegal (encoding of) characters that might be used in the text you are copy-pasting from .. for instance, this is correct:

cout << "Hello!" << endl;


..while this is not:


cout << &#8220;Hello!&#8221; << endl;


..note how &#8220; and &#8221; are not the same character as the (correct) " ..  it is very hard to see visually here with this font .. here is a screenshot:

[IMG]http://nostdal.org/~lars/stray-characters.png[/IMG]

..the second one is correct .. (shift 2)

---

### Post by mills on 2007-03-11
@darkness 

yeah i edfinately got essential build installed and tried your code after changing filename

alex@alex-desktop:~$ g++ -o help -g -Wall help.cpp
help.cpp:11: error: stray &#8216;\302&#8217; in program
help.cpp:11: error: stray &#8216;\240&#8217; in program
help.cpp:11: error: stray &#8216;\302&#8217; in program
help.cpp:11: error: stray &#8216;\240&#8217; in program
help.cpp:11: error: stray &#8216;\302&#8217; in program
help.cpp:11: error: stray &#8216;\240&#8217; in program
help.cpp:11: error: stray &#8216;\302&#8217; in program
help.cpp:11: error: stray &#8216;\240&#8217; in program
help.cpp:11: error: stray &#8216;\302&#8217; in program
help.cpp:11: error: stray &#8216;\240&#8217; in program
help.cpp:12: error: stray &#8216;\302&#8217; in program
help.cpp:12: error: stray &#8216;\240&#8217; in program
help.cpp:12: error: stray &#8216;\302&#8217; in program
help.cpp:12: error: stray &#8216;\240&#8217; in program
help.cpp:12: error: stray &#8216;\302&#8217; in program
help.cpp:12: error: stray &#8216;\240&#8217; in program
help.cpp:12: error: stray &#8216;\302&#8217; in program
help.cpp:12: error: stray &#8216;\240&#8217; in program
help.cpp:12: error: stray &#8216;\302&#8217; in program
help.cpp:12: error: stray &#8216;\240&#8217; in program

same story:( 

@inostdal, the source is copied from an ebook (addison wesley-accelarated c++) and ive double checked so cant be a syntax error

ps, yeah sorry about the messy code,

---

### Post by lnostdal on 2007-03-11
it's not syntax error in the "traditional sense" .. it's encoding error of characters .. this is not something i'm mistaken about, trust me .. it can even be invisible characters .. view it in a combined hex/ascii editor to confirm it yourself if you need to

---

### Post by mills on 2007-03-11
know any good combined hex/ascii editor's :)

and also, does this mean i cant copy and paste code from an ebook into gedit?

---

### Post by lnostdal on 2007-03-11
> **mills said:**
> know any good combined hex/ascii editor's :)

emacs ..   googling also reveals ghex (but i haven't tried it .. it seems to be in the ubuntu repos though)

[quote=mills]
and also, does this mean i cant copy and paste code from an ebook into gedit?[/QUOTE]

in this case; yes .. in general; no

in this case you will probably need to hunt down the stray characters and delete them or replace them with the correct characters

---

### Post by Darkness3477 on 2007-03-11
Hmmm.. Well, lnostdal knows a hell of a lot more about this stuff then me, so he should be able to clear it up for you. All I know is it worked for me.

I tried copying a game example in Python out of a (free) ebook, and it used 1.5 spacing, which made python spit out syntax errors. I got rid of it by highlighting his 1.5 spacing, copying it and pasting it into replace feature in gedit. Copy it in there and replace it with the standard value. 

Dunno if that'll help you at all, but it's what I did in a similar situation.

P.S. Where did you get that book from? Also, is it any good. I have a c++ book for dummies. The writer explains things so well, but I don't think the actual code examples are all that great.

---

### Post by lnostdal on 2007-03-11
you can of course download the source code for the book: [http://www.acceleratedcpp.com/](http://www.acceleratedcpp.com/)

---

### Post by mills on 2007-03-11
@ darkness, i downloaded "500 computer books" from a torrent site which had about 60-70 c++ books in it, dunno if this book in particular is any good yet but it's been reccomended a few times so iam trying it

@ inostdal, i havent gone down the emacs road yet, i thought maybe it would be better to just write the code in there myself to get a better understanding as i learn but i get the same errors

surely this mean's the problem doesnt involve copy and pasting,

---

### Post by lnostdal on 2007-03-11
it means you're somehow inserting or having illegal characters in the code

here: [http://nostdal.org/~lars/programming/c/hello.cpp](http://nostdal.org/~lars/programming/c/hello.cpp)

if you have further problems you can upload the file as an attachment in the forum (edit: at least i think it is possible to upload attachments?)

---

### Post by mills on 2007-03-11
nah cant figure this out inostdal, cheers for the help but i reckon an ide is the way to go

---

### Post by lnostdal on 2007-03-11
lol .. ok

---

### Post by jenkinbr on 2008-04-04
I know this is waay out of date, but I have found a cause and a solution to the above mentioned problems.  You mention the compiler generating errors like the following:
```

foo.cpp:11: error: stray &#8216;\302&#8217; in program
foo.cpp:11: error: stray &#8216;\240&#8217; in program
foo.cpp:11: error: stray &#8216;\302&#8217; in program
foo.cpp:11: error: stray &#8216;\240&#8217; in program
foo.cpp:11: error: stray &#8216;\302&#8217; in program
foo.cpp:11: error: stray &#8216;\240&#8217; in program
foo.cpp:11: error: stray &#8216;\302&#8217; in program
foo.cpp:11: error: stray &#8216;\240&#8217; in program
foo.cpp:11: error: stray &#8216;\302&#8217; in program
foo.cpp:11: error: stray &#8216;\240&#8217; in program
foo.cpp:12: error: stray &#8216;\302&#8217; in program
foo.cpp:12: error: stray &#8216;\240&#8217; in program
foo.cpp:12: error: stray &#8216;\302&#8217; in program
foo.cpp:12: error: stray &#8216;\240&#8217; in program
foo.cpp:12: error: stray &#8216;\302&#8217; in program
foo.cpp:12: error: stray &#8216;\240&#8217; in program
foo.cpp:12: error: stray &#8216;\302&#8217; in program
foo.cpp:12: error: stray &#8216;\240&#8217; in program
foo.cpp:12: error: stray &#8216;\302&#8217; in program
foo.cpp:12: error: stray &#8216;\240&#8217; in program

```
Like you, I also type my code into gedit, and run g++ to compile.

The problem is what I beleive to be a non-breaking space, caused by holding [shift] while pressing [space].  I often do it on accident when typing the insertion and extration operators "<<" and ">>"

The fix?  In gedit, open the find and replace dialogue, and in the find box, hold [shift] and hit [space].  In the replace with box, enter a single space.  Hit find, verify that there is nothing selected that shouldn't be, and hit replace all.

Me and several college instructors spent 5 weeks  tearing our hair out over this (invisible) issue.
Hope this helps others who have this issue.

btw, I've ported good (simple) code from windows to ubuntu and vice versa without issue.

---

### Post by vincesoh on 2008-10-20
Hi, I'm just new to Ubuntu. But somehow, I had face this type of question in C programming also.

At 1st, I straight copy the example code from tutorial and paste into the text editor, save as 'test.c'. Then when I compile, it shows that

vince@vince-laptop:~/Desktop$ gcc test.c -o test
test.c: In function ‘main’:
test.c:15: error: stray ‘\302’ in program
test.c:15: error: stray ‘\240’ in program
test.c:16: error: stray ‘\302’ in program
test.c:16: error: stray ‘\240’ in program
test.c:16: warning: incompatible implicit declaration of built-in function ‘exit’
test.c:19: error: stray ‘\302’ in program
test.c:19: error: stray ‘\240’ in program
test.c:19: warning: incompatible implicit declaration of built-in function ‘printf’
test.c:20: error: stray ‘\302’ in program
test.c:20: error: stray ‘\240’ in program
test.c:28: error: stray ‘\302’ in program
test.c:28: error: stray ‘\240’ in program
test.c:31: error: stray ‘\302’ in program
test.c:31: error: stray ‘\240’ in program
test.c:32: error: stray ‘\302’ in program
test.c:32: error: stray ‘\240’ in program
test.c:32: warning: incompatible implicit declaration of built-in function ‘exit’
test.c:35: error: stray ‘\302’ in program
test.c:35: error: stray ‘\240’ in program
test.c:36: error: stray ‘\302’ in program
test.c:36: error: stray ‘\240’ in program
test.c:38: error: stray ‘\302’ in program
test.c:38: error: stray ‘\240’ in program

The source code is:

#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#define MYPORT 3334

int main()
{
int sockfd;  /* socket file descriptor */
struct sockaddr_in my_addr;

sockfd = socket(AF_INET, SOCK_STREAM, 0);
if((sockfd = socket(AF_INET, SOCK_STREAM, 0)) == -1)
{
  perror("Server-socket() error lol!");
  exit(1);
}
else
* printf("Server-socket() sockfd is OK...\n");
*
/* host byte order */
my_addr.sin_family = AF_INET;
/* short, network byte order */
my_addr.sin_port = htons(MYPORT);
my_addr.sin_addr.s_addr = INADDR_ANY;
/* zero the rest of the struct */
memset(&(my_addr.sin_zero), 0, 8);
*
if(bind(sockfd, (struct sockaddr *)&my_addr, sizeof(struct sockaddr)) == -1)
{
* perror("Server-bind() error lol!");
* exit(1);
}
else
* printf("Server-bind() is OK...\n");
*
/*....other codes....*/
*
return 0;
}

But after I change all the line that start with " "(white space) to "     "(single tab), the file can be compile and work. lol


#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#define MYPORT 3334

int main()
{
int sockfd;  /* socket file descriptor */
struct sockaddr_in my_addr;

sockfd = socket(AF_INET, SOCK_STREAM, 0);
if((sockfd = socket(AF_INET, SOCK_STREAM, 0)) == -1)
{
	perror("Server-socket() error lol!");
	exit(1);
}
else
	printf("Server-socket() sockfd is OK...\n");

/* host byte order */
my_addr.sin_family = AF_INET;
/* short, network byte order */
my_addr.sin_port = htons(MYPORT);
my_addr.sin_addr.s_addr = INADDR_ANY;
/* zero the rest of the struct */
memset(&(my_addr.sin_zero), 0, 8);

if(bind(sockfd, (struct sockaddr *)&my_addr, sizeof(struct sockaddr)) == -1)
{
	perror("Server-bind() error lol!");
	exit(1);
}
else
	printf("Server-bind() is OK...\n");

/*....other codes....*/

return 0;
}


Hope this may help you.

---

### Post by Malifice on 2009-06-08
> **jenkinbr said:**
> I know this is waay out of date, but I have found a cause and a solution to the above mentioned problems.  You mention the compiler generating errors like the following:
```

foo.cpp:11: error: stray ‘\302’ in program
foo.cpp:11: error: stray ‘\240’ in program
...

```
Like you, I also type my code into gedit, and run g++ to compile.

The problem is what I beleive to be a non-breaking space, caused by holding [shift] while pressing [space].  I often do it on accident when typing the insertion and extration operators "<<" and ">>"
...

THANK YOU!

I know it's an Unbuntu forum, but if there someone out there using MacOS the non-breaking space is obtained by holding SHIFT+ALT+SPACE. (yeah my fingers are heavy...)

---

### Post by jenkinbr on 2009-06-08
> **Malifice said:**
> THANK YOU!

I know it's an Unbuntu forum, but if there someone out there using MacOS the non-breaking space is obtained by holding SHIFT+ALT+SPACE. (yeah my fingers are heavy...)
Wow this thread is old.

You're welcome!  I'm glad it worked for you.  G++ doesn't like non-breaking spaces for some reason.

---

### Post by tnjed111 on 2009-06-15
I don't know what the problem was for me but I was getting the same stray ‘\302’ and '\240' problem. 
I found this shell command, which apparently removes all characters except printable ASCII and spaces and newlines, so that what you are left with is a text file that will compile, although you lose some formatting such as indentation. 
(I was pasting from an ebook, too.)
Anyway, try:

tr -cd '\11\12\40-\176' < $INPUT_FILE > $OUTPUT_FILE

(the '<' and '>' are necessary)

It has worked for me a bunch of times. And yes, the input and output files have to be different or it won't work.

---

### Post by kedarkekan on 2010-01-25
Hi Guys,

I got the same issue ...... I am using Ubuntu 9.10 desktop in VM Ware ...

Plz help ...


#include<iostream>


using namespace std;

int main()
{
cout<<¨test¨<<endl;   // the line where i get error

return 0;

}


I tried few of the tricks mentioned above but none of them work ...

Is there any special treatment for VM Player ??

---

### Post by Garratt on 2010-01-25
read page two
the solution is there... you can find replace the dodgy characters in gedit or whatever your using and replace with a normal " " space

I typically do this all the time and have never had this problem so i'm guessing it's a gedit bug (or strange default encoding) that needs to be reported. (I don't use gedit), IDE or vim.

---

### Post by kedarkekan on 2010-01-27
> **Garratt said:**
> read page two
the solution is there... you can find replace the dodgy characters in gedit or whatever your using and replace with a normal " " space

I typically do this all the time and have never had this problem so i'm guessing it's a gedit bug (or strange default encoding) that needs to be reported. (I don't use gedit), IDE or vim.
Well I tried to use Gvim, emacs, gedit ....also found that the character which gives error is double quotes (")  ... 

Problem is that i have to press my shift+double quotes key twice to get (") on the screen.


I tried to delete & again type the (") from all three editors abov; but all in vain.

I just can't do any programming without (") in my code :(

I am using ubuntu 9.10 in VM Ware....
plz help....

---

### Post by dwhitney67 on 2010-01-27
What type of terminal is VM ware emulating?

---

### Post by kedarkekan on 2010-01-29
> **dwhitney67 said:**
> What type of terminal is VM ware emulating?
I am using VM Ware Player 3.0 and Ubuntu 9.10 desktop application (downloaded from VM Ware website)......

---

### Post by kedarkekan on 2010-01-29
> **dwhitney67 said:**
> What type of terminal is VM ware emulating?
VMware info
- Date of creation: 12 January 2010
- CPUs : 1
- RAM : 512 MB
- Networking : NAT
- Harddisk : 20 GB SCSI (expanding)
- VMware tools : Installed
 OS info
- OS : Ubuntu 9.10 Desktop
- Installation : Standard
- Hostname : ubuntu910desktop
- Patches : till date of creation
- IPv4 address : dhcp
- IPv6 address : dhcp
- DNS name : none
- Nameserver : dhcp
- Route : dhcp
- Keyboard : US_intl

---

### Post by kedarkekan on 2010-01-29
> **kedarkekan said:**
> VMware info
- Date of creation: 12 January 2010
- CPUs : 1
- RAM : 512 MB
- Networking : NAT
- Harddisk : 20 GB SCSI (expanding)
- VMware tools : Installed
 OS info
- OS : Ubuntu 9.10 Desktop
- Installation : Standard
- Hostname : ubuntu910desktop
- Patches : till date of creation
- IPv4 address : dhcp
- IPv6 address : dhcp
- DNS name : none
- Nameserver : dhcp
- Route : dhcp
- Keyboard : US_intl
Hey guys found the solution ......  with help of my friend Rishi (who is on work tour in South Korea :P )

Well it is all to do with your keyboard setting and preferences :-

Change/Add the layout to:

Country: USA
Variants: USA 


Remove the default one; wherein the variant comes with some "dead key options"
....that kills your double quotes (")  :P


All works fine with Gvim now :)

---

