---
title: "Unicode problems in C"
date: 2010-07-04
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-07-04
I want to be able to type faster, so I have used typespeed for practicing before. But I want to make a better typing program, with full unicode support.
 
I have piece of code to read key presses without waiting for carriage return (got the code from [http://groups.google.com/group/comp.os.linux.development/browse_thread/thread/d3d0b4ff5a40dec7):](http://groups.google.com/group/comp.os.linux.development/browse_thread/thread/d3d0b4ff5a40dec7):)
```

#include <termios.h>
#include <unistd.h> 
#include <wchar.h>

...

static wchar_t get_key()
{
	struct termios argin, argout;
	wchar_t ch = 0; 
	tcgetattr( 0,&argin );
	argout = argin;
	argout.c_lflag &= ~(ICANON);
	argout.c_iflag &= ~(ICRNL);
	argout.c_oflag &= ~(OPOST);
	argout.c_cc[VMIN] = 1;
	argout.c_cc[VTIME] = 0;
	tcsetattr( 0,TCSADRAIN,&argout );
	read( 0, &ch, sizeof(ch) );
	tcsetattr( 0,TCSADRAIN,&argin );
	return ch;
}

```
[COLOR="Gray"](I don't usually copy-paste-modify code from the internet but I couldn't figure that out myself.)[/COLOR]

I have a finnish keyboard, which has keys for ä and ö. 

It's not possible to get ä nor ö with the function above (they show up as &#46787; and &#42179;). 

How to read unicode characters (without waiting for carriage return)?

---

### Post by mmix on 2010-07-04
slightly offtopic, try libutf from p9p

[http://swtch.com/plan9port/unix/](http://swtch.com/plan9port/unix/)

---

### Post by dwhitney67 on 2010-07-04
You should consider using getwchar() and putwchar().  As for controlling the input-blocking of standard-in, this should be done separately from the step to read input.

Try this app:
```

#include <stdio.h>
#include <termios.h>
#include <unistd.h>
#include <string.h>

// For yesOrNo, 1 is to enable non-blocking, 0 to disable (ie blocking).
int enableNonBlocking(int yesOrNo, int fileno)
{
   static struct termios old;

   if (yesOrNo)
   {
      struct termios tmp;

      if (tcgetattr(fileno, &old))
      {
         return -1;
      }

      memcpy(&tmp, &old, sizeof(old));

      tmp.c_lflag &= ~ICANON & ~ECHO;

      if (tcsetattr(fileno, TCSANOW, (const struct termios*) &tmp))
      {
         return -1;
      }
  }
  else
  {
     tcsetattr(fileno, TCSANOW, (const struct termios*) &old);
  }

  return 0;
}

// Main
//
#include <wchar.h>

int main()
{
   enableNonBlocking(1, STDIN_FILENO);

   printf("Enter a sentence ending with a .:\n");

   wint_t ch = WEOF;

   while ((ch = getwchar()) != '.')
   {
      putwchar(ch);
   }
   putwchar(ch);
   puts("");

   enableNonBlocking(0, STDIN_FILENO);

   return 0;
}

```

---

### Post by crazyfuturamanoob on 2010-07-04
I solved it on my own:
```

int _get_key()
{
	struct termios argin, argout;
	int ch = 0; 
	tcgetattr( 0,&argin );
	argout = argin;
	argout.c_lflag &= ~(ICANON);
	argout.c_iflag &= ~(ICRNL);
	argout.c_oflag &= ~(OPOST);
	argout.c_cc[VMIN] = 1;
	argout.c_cc[VTIME] = 0;
	tcsetattr( 0,TCSADRAIN,&argout );
	read( 0, &ch, sizeof(ch) );
	tcsetattr( 0,TCSADRAIN,&argin );
	return ch;
}

wchar_t get_key()
{
	char buf_src[16] = {0};
	int x = _get_key();
	memcpy( buf_src, &x, sizeof(x) );
	
	wchar_t buf_dest[16] = {0};
	mbstowcs( buf_dest, buf_src, 1 );
	
	return buf_dest[0];
}

```
ä and ö work! :D:D:D

---

### Post by dwhitney67 on 2010-07-04
That seems like a lot of code to read just one (wide) character.  Consider simplifying it a bit before you consider yourself done with the task.

---

### Post by crazyfuturamanoob on 2010-07-04
I use my own "GUI" library, which allows reading and writing characters as if they were pixels. [s]Edit: Your code works too so I use it.[/s] Thanks :)

I rewrote the function. Looks much more readable IMO:
```

int enable_non_blocking( int nonblocking, int fileno )
{
	static struct termios old;
	struct termios tmp;
	
	if ( nonblocking )
	{
		if ( tcgetattr( fileno, &old ) )
			return 0;
		
		memcpy( &tmp, &old, sizeof(old) );
		tmp.c_lflag &= ~ICANON & ~ECHO;
		
		if ( tcsetattr( fileno, TCSANOW, (const struct termios*) &tmp ) )
			return 0;
	}
	else
		tcsetattr( fileno, TCSANOW, (const struct termios*) &old );
	
	return 1;
}

```

Edit2: There is one problem: Pressing return will mess up terminal window. My GUI library doesn't work in non-blocking mode.
Edit3: And another problem. If the program segfaults, terminal will be in non-blocking mode and is completely unusable.

My solution doesn't look pretty but works better.

---

