---
title: "installing eclipse"
date: 2008-01-31
forum: Packaging and Compiling Programs
---

### Post by EYALf on 2008-01-31
I've just installed eclipse and when I tried to compile this program it says: "osgi> "

this is the program i'm trying to run:

/*This program calculates the validation digit of an ID number.
The ID number has at most 8 digits (it can have less).*/

class Id{
	public static void main (String[] args){
		int id,id1,digit=0;
		int i=0,sum=0;
		id = Console.readInt("Enter an ID number without the validation digit:");
		id1=id;
		for (i=0;i<=7;i++) 
			{
				digit=id%10;
				id=id/10;
				if (i%2==0)
					{
						digit=digit*2;
						if (digit>=10)
							{
								digit=digit%10+digit/10;
							}
					}
				sum=sum+digit;
			}
					
		digit=(10-sum%10); 
		
		System.out.println("The sum is "+sum);
		System.out.println("The validation digit of "+id1+" is "+digit+"." );
	}
}

One more thing. in Eclipse when I write Print.out.println, the "out" comes clue and leans to the left. does it mean anything?

I guess I'm looking for a tutorial for installing Eclipse...
Thanks.

---

### Post by Shin_Gouki2501 on 2008-01-31
???
apt-get install eclipse did not work?!

---

### Post by EYALf on 2008-01-31
> **Shin_Gouki2501 said:**
> ???
apt-get install eclipse did not work?!

this is what i got when i typed what you said:
eyal@eyal-desktop:~$ apt-get install eclipse
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
eyal@eyal-desktop:~$ 


what now?

---

### Post by Compyx on 2008-01-31
You need elevated privileges to run apt-get, try:
```
sudo apt-get install eclipse
```

---

### Post by EYALf on 2008-01-31
> **Compyx said:**
> You need elevated privileges to run apt-get, try:
```
sudo apt-get install eclipse
```

**ok this is the output after I did what you wrote:**
eyal@eyal-desktop:~$ sudo apt-get install eclipse
[sudo] password for eyal:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
eclipse is already the newest version.
The following packages were automatically installed and are no longer required:
  texlive-common texlive-doc-base tex-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eyal@eyal-desktop:~$ 

It appears like nothing is changed... still the same problem.

---

### Post by lsmobrian on 2008-01-31
just checking but make sure you have a java compiler installed, you obviously have a jre installed if youre running eclipse, but you also need a jdk to compile.   in a terminal, type 'javac'  it will either print out a description of how to use javac or it will tell you a compiler is not installed and then hopefully it will give you a list of compilers, install one (icedtea or sun6)



id = Console.readInt("Enter an ID number without the validation digit:");

assuming you are importing Console and just didnt list your imports or Console is another class in your src directory?



One more thing. in Eclipse when I write Print.out.println, the "out" comes clue and leans to the left. does it mean anything?

I have no clue what you mean by this, sorry.  Could you elaborate? 
(did you mean System.out.println)

---

### Post by EYALf on 2008-02-01
> **lsmobrian said:**
> just checking but make sure you have a java compiler installed, you obviously have a jre installed if youre running eclipse, but you also need a jdk to compile.   in a terminal, type 'javac'  it will either print out a description of how to use javac or it will tell you a compiler is not installed and then hopefully it will give you a list of compilers, install one (icedtea or sun6)



id = Console.readInt("Enter an ID number without the validation digit:");

assuming you are importing Console and just didnt list your imports or Console is another class in your src directory?



One more thing. in Eclipse when I write Print.out.println, the "out" comes clue and leans to the left. does it mean anything?

I have no clue what you mean by this, sorry.  Could you elaborate? 
(did you mean System.out.println)

Thanks for your help first.
I thought it maybe better if I attached some images.

In Id you see what I ment that the "out" comes blue..

I installed sun6-like you said- but still nothing is changed.

When I want to debug a program, a window opens. I'm not really sure what am I suppose to choose so I attached this as well("debug").

Again, thanks for your help.

---

### Post by Shin_Gouki2501 on 2008-02-01
explain a bit what u want to debug?!
Or what u want to try out?!
Please u need to speak a bit more!
if u want to debug u need to specify a debug point before that!

---

### Post by EYALf on 2008-02-01
thanks I found out what ws missing... thanks!

---

