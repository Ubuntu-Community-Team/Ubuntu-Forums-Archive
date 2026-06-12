---
title: "Taking user input without it showing on screen? Using C"
date: 2014-11-11
forum: Programming Talk
---

### Post by SagaciousKJB on 2014-11-11
I wrote up myself a little password manager in C.  The goal was to be completely portable between Windows and Linux and not require an libraries.  All it does is modify files in a certain format ( entry name : password ) and I can store multiples entries in the same files--so for example I have one for my forum-name passwords and another for email accounts, and I just use an easy-to-remember pass to encrypt the file (using just XOR encryption) with stronger passwords.  Makes it easy to use strong passwords, but access with an easier one to remember--but since it's not very wise to store passwords in plain-text I needed encryption and the manager to read the files.

There's just one problem..  How do I keep myself from having to enter the so-called "master" easy-to-remember password on the command line to access the rest?  The only reason I have encryption is because I like to store the files on a thumbstick ( portable ) and don't want someone discovering my plain-text passwords--but I also like to think it's a nice precaution in case I'm using a computer infected with a virus that might be looking for passwords.  I'm not you know, a target of the NSA so I haven't felt the need for anything stronger than XOR, I'm just interested in obfuscation to keep out normal people but I feel like leaving the "master" pass on the command line is just defeating the whole purpose.  Especially if I leave it on a public computer--up until now I've just manually erased command history, at least as much as I knew how or had the permission to edit.  I used the program on school computers that could have logged all of my commands on a remote server for all I know.

I feel like the simplest solution would be to just prompt the user to enter the password and read it from the program via standard input.  Just one more problem: I don't know how to mask the user input text.  Take a program like "sudo" for example, it prompts the user for the password but when they type, it doesn't appear on the screen at all.  I'd like to duplicate that type of behavior but don't really know how, and also is there a way to do it that will be platform independent?

I use to keep a Windows binary and my passwords on a thumbstick since that's where I would mostly encounter the need to have a more secure method of password entry.

---

### Post by TheFu on 2014-11-11
KeePass v1.x  and KeePassX v1.x solves this with greater security. The code for both is open - grab a copy, look through it, see how they handle passwords.  Please.

Anything included on the command line is available in the process table to anyone on the system. Just sayin'.

However, there are routines to accept passwords - find one of those for your needs.  
[https://stackoverflow.com/questions/6856635/hide-password-input-on-terminal](https://stackoverflow.com/questions/6856635/hide-password-input-on-terminal)

XOR isn't even obfuscation. For a 1st semester programmer, I suppose it is fine. Even the Caesar cipher would be better and that sucks too.

---

### Post by SagaciousKJB on 2014-11-12
> **TheFu said:**
> KeePass v1.x  and KeePassX v1.x solves this with greater security. The code for both is open - grab a copy, look through it, see how they handle passwords.  Please.

Anything included on the command line is available in the process table to anyone on the system. Just sayin'.

However, there are routines to accept passwords - find one of those for your needs.  
[https://stackoverflow.com/questions/6856635/hide-password-input-on-terminal](https://stackoverflow.com/questions/6856635/hide-password-input-on-terminal)

XOR isn't even obfuscation. For a 1st semester programmer, I suppose it is fine. Even the Caesar cipher would be better and that sucks too.

It's a little bit more complex than byte = byte XOR byte but I didn't want to exaggerate by calling it "encryption".  It operates more as a Viegenere cipher with a one-time-pad--but cryptographically flawed as it is NOT a one-time-pad.  I'm pretty confident no one short of a crytpanalyst that finds it would be able to crack it.  You're welcome to give it a try if you'd like. ;)  I thought about implementing an open source method but didn't want to have to include more libraries.

I may try out KeePass anyway though.  I like the GUI and the other features.  Is the port for Linux stable?

---

### Post by TheFu on 2014-11-12
Is that really a question, stable?  
Also, I don't use KeePass on Linux. Hate Mono, won't have it on my systems.  I use KeePassX and find it mostly awesome.  For me, having extremely strong encryption is so much easier than trying to roll my own - why bother?  There are valid reasons, just not for me.

Be careful on the DB versions - make certain you pick the version that is compatible across all the platforms you require.

Write your own algorithm. Analyze it, test it, share with others. But when using one, use a well designed and tested algorithm.
*Applied Cryptography* is required reading in this space. I'm sure you know that already.

---

### Post by SagaciousKJB on 2014-11-12
> **TheFu said:**
> Is that really a question, stable?  
Also, I don't use KeePass on Linux. Hate Mono, won't have it on my systems.  I use KeePassX and find it mostly awesome.  For me, having extremely strong encryption is so much easier than trying to roll my own - why bother?  There are valid reasons, just not for me.

Be careful on the DB versions - make certain you pick the version that is compatible across all the platforms you require.

Write your own algorithm. Analyze it, test it, share with others. But when using one, use a well designed and tested algorithm.
*Applied Cryptography* is required reading in this space. I'm sure you know that already.

Yeah cryptography is kind of a hobby interest of mine, I don't pretend to be an expert in the least.  Maybe down the line though I can think of a way to implement a more standard algorithm like blowfish but for now even using the OpenSSL libraries for it has been kind of "above my head", and even that would reduce my desired portability.  So I've had my own home-brewed algorithm for a number of years anyway, and just decided to use that for the password manager--like I said my main concern is losing my thumbstick and having a bunch of files that have my passwords.  My algorithm basically XORs a repeated user-inputed string along with the plain-text and a number of other variables including the length of the plain text, and of the string.  I really doubt it'd be much of a challenge to someone that knew what they were doing, but I hardly think I'm worth the effort for anyone to try :P

Thanks for the link!  Managed to whip up what I think should be a good cross-platform solution.  If on a Windows machine it will just use the getch() in conio.h, on Linux one of the methods posted up there.

```

/*portablegetch.h*/
#ifndef PGETCH
#define PGETCH
#ifdef __unix__
#include <termios.h>
#include <unistd.h>

static struct termios n_term;
static struct termios o_term;

static int
cbreak(int fd) 
{
   if((tcgetattr(fd, &o_term)) == -1)
      return -1;
   n_term = o_term;
   n_term.c_lflag = n_term.c_lflag & ~(ECHO|ICANON);
   n_term.c_cc[VMIN] = 1;
   n_term.c_cc[VTIME]= 0;
   if((tcsetattr(fd, TCSAFLUSH, &n_term)) == -1)
      return -1;
   return 1;
}

int getch() 
{
   int cinput;

   if(cbreak(STDIN_FILENO) == -1) {
      fprintf(stderr, "cbreak failure, exiting \n");
      exit(EXIT_FAILURE);
   }
   cinput = getchar();
   tcsetattr(STDIN_FILENO, TCSANOW, &o_term);

   return cinput;
}

#elif _MSC_VER  || __WIN32__ || __MS_DOS__
  #include <conio.h>
#endif
#endif

#define BACK_SPACE 127

char* my_getpass(void) 
{
	int i=0;
	char *pass, c;
	pass = malloc(sizeof(char) * 256);
	if(pass == NULL)
	{
		exit(1);
	}

	while((c=getch()) != '\n')
	{
		if(c == BACK_SPACE)
		{
			i--;
			printf("\b \b");
		}
		else
		{
			pass[i] = c;
			printf("*");
			i++;
		}
	}
	pass[i] = '\0';

	return pass;

}

```

Now, will I need to compile that from an actual Windows environment or can I just use the mingw32 runtime?

If you're interested in giving me a critique or checking out my algorithm, I tried posting that but I don't think the forum liked all the text :/

---

### Post by TheFu on 2014-11-12
Buffer overflow will be trivial.
Initialize all variables to known values.
I'd also swap the comparisons with the static value to always be on the lefthandside of the comparison. Defensive programming techniques.

I'm still confused why you aren't using the built-in password getting routines - those are cross platform.

---

### Post by SagaciousKJB on 2014-11-12
> **TheFu said:**
> Buffer overflow will be trivial.
Initialize all variables to known values.
I'd also swap the comparisons with the static value to always be on the lefthandside of the comparison. Defensive programming techniques.

I'm still confused why you aren't using the built-in password getting routines - those are cross platform.

Which ones do you mean?  I only read about getpass() (unistd.h) but the man page says it is obsoleted.

---

### Post by TheFu on 2014-11-12
> **SagaciousKJB said:**
> Which ones do you mean?  I only read about getpass() (unistd.h) but the man page says it is obsoleted.

So - my knowledge is outdated - it is from the 1990s when my team wrote commercial cross-platform software. Someone must have written a cross-platform no-echo routine since that point. Googling ... 

Google-fu found this: [https://stackoverflow.com/questions/1196418/getting-a-password-in-c-without-using-getpass-3](https://stackoverflow.com/questions/1196418/getting-a-password-in-c-without-using-getpass-3)

---

### Post by SagaciousKJB on 2014-11-12
> **TheFu said:**
> So - my knowledge is outdated - it is from the 1990s when my team wrote commercial cross-platform software. Someone must have written a cross-platform no-echo routine since that point. Googling ... 

Google-fu found this: [https://stackoverflow.com/questions/1196418/getting-a-password-in-c-without-using-getpass-3](https://stackoverflow.com/questions/1196418/getting-a-password-in-c-without-using-getpass-3)

Looks pretty similar to what I found on the Linux end, but not on the Windows side...  Could explain why it's not working correctly on Windows 7.  Almost, it just doesn't ever "end" the input when I press enter. I feel like I'm just forgetting how to test for end-of-input on Windows correctly though :/

Ahh yeah, pesky "\r".  I've got it working now.   Thanks for your help :)

---

