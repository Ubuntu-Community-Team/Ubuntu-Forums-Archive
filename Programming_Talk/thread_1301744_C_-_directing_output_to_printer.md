---
title: "C - directing output to printer"
date: 2009-10-26
forum: Programming Talk
---

### Post by Jim_in_Germany on 2009-10-26
Hi,
I'm reading a book about C and am stuck on a section regarding how to send text directly to the printer (as opposed to the screen).

I have:

```
#include <stdio.h>

main()
{
FILE *printer = fopen("/dev/usb/lp0", "w");
fprintf(printer, "Hello World.");
fclose(printer);
return 0;
}

```
When I compile and run the program using gcc, my printer light flashes, but nothing else happens.

When I add the line:
```
fprintf(printer, "\f");
```

then my printer prints out a blank page.

What am I doing wrong?
Am grateful for any help, but please bear in mind I am a beginner in C.

---

### Post by dwhitney67 on 2009-10-26
You may need to fflush() the output.

What results do you get with:
```

#include <stdio.h>

main()
{
FILE *printer = fopen("/dev/usb/lp0", "w");
fprintf(printer, "Hello World.**\n\f**");
**fflush(printer);**
fclose(printer);
return 0;
}

```

---

### Post by Jim_in_Germany on 2009-10-26
Hi,
Thanks for the reply.
I compiled and ran the code you suggested and unfortunately the printer just spat out a blank page.
This seems to be caused by the "\f" character.
I also just tried printing something from the text editor to make sure that it is not the printer at fault and this worked fine :-(
Any ideas?

---

### Post by dwhitney67 on 2009-10-26
I looked into an application I wrote over 11 years ago under Solaris, and I must've had the same problem you are experiencing.  In the code, I placed a comment that sending data to the printer does not work as "gracefully" as one would hope.  My cheesy solution was to output the data to a file, and then using the system() library call, I was able to call "lp".

Sorry I cannot help more.

---

### Post by Tony Flury on 2009-10-26
I would imagine most "modern" printers do not expect just straight Ascii text, and that the drivers generate something altogether more complex.

I don't think you can send a text file for instance direct to "/dev/usb/lp0" - you need to go via the printer driver - i.e. lp.

using lp sounds like a good idea to me - as you would then us the preferences that the user has set up - instead of your application over-riding them.

---

### Post by Jim_in_Germany on 2009-10-26
Thanks for your answer..
I have been playing around with this and googling all evening and am unfortunately still no closer to solving my problem.
What is irritating me is that I am obviously able to connect to the printer in some way as it will chuck out a blank page when I send it:
```
fprintf(printer, "\f");
```
If anyone else has any ideas then I'd be grateful.
Thanks in advance.

---

### Post by Jim_in_Germany on 2009-10-26
> **Tony Flury said:**
> I would imagine most "modern" printers do not expect just straight Ascii text, and that the drivers generate something altogether more complex.

I don't think you can send a text file for instance direct to "/dev/usb/lp0" - you need to go via the printer driver - i.e. lp.

using lp sounds like a good idea to me - as you would then us the preferences that the user has set up - instead of your application over-riding them.

That seems like it makes sense. I found various ways to send output to the printer in C, ranging from 'stdprn', to 'PRN' to 'LPT1:' to '/dev/lp1'
Everything I can find online however, points to this being rather dated.
Could you give me a hint as to what the command would look like to send output via the printer driver?
I tried this, without success:
```
FILE *printer = fopen("lp0", "w");
```

---

### Post by Tony Flury on 2009-10-26
I would use the idea of dumping your output to a text file and then using the lp command to print it.

---

### Post by Simian Man on 2009-10-26
This kind of thing is fine for just messing around, but a serious application that wants to print should never even think of talking to the printer directly like this.  Instead you should use a printing API that abstracts away the actual printer device.

The only time I've printed from an application, I used wxWidgets which handled it all rather simply.

---

### Post by fct on 2009-10-26
The "\f" is a form feed, it ejects the page and gets another.

Try this:

```


#include <stdio.h>

int main(int argc, char **argv)
{
        FILE *printer = popen("/usr/bin/lpr -P PDF", "w");

        if (printer == NULL)
                return 1;
        
        printf("OK\n");
        fprintf(printer, "alsdjakljdlaskjd\n");
        pclose(printer);
        return 0;
}

```

Note "-P PDF" sets the printer. In my case I have installed "cups-pdf" to test it by printing to a pdf file (I have no printer here anyway).

You can see the list of printers with the "lpinfo" command.

---

### Post by Jim_in_Germany on 2009-10-27
Hey, that works (minus the -P PDF of course).
Thanks very much.
I was working on a similar solution in Ruby and had got as far as calling "lpr" either like so ```
exec "echo \"hi\" | lpr"
``` or like so ```
`echo "Hello" | lpr`
```
It hadn't occured to me to open a pipe to lpr and to stick everything in that.

Can I just ask a couple of questions about your code?

```
FILE *printer = popen("/usr/bin/lpr", "w");
```
Would it be correct to say that this line opens a pipe to "/usr/bin/lpr" in write mode, then creates a pointer with the name 'printer' and of the type FILE and assigns the pointer to a stream that can be used to write to the pipe?

```
int main(int argc, char **argv)
```
argc = argument count
argv = argument value
Why is it necessary to list them here, as main doesn't have any parameters per-say? 
What does the double star in front of argv denote?

Thanks again for your help.

---

### Post by benj1 on 2009-10-27
> **Jim_in_Germany said:**
> 
Can I just ask a couple of questions about your code?

```
FILE *printer = popen("/usr/bin/lpr", "w");
```
Would it be correct to say that this line opens a pipe to "/usr/bin/lpr" in write mode, then creates a pointer with the name 'printer' and of the type FILE and assigns the pointer to a stream that can be used to write to the pipe?

yes its essentially your first example except treating the printer as a pipe rather than a file, im not sure why you have to do it like this, everything is supposed to be a file, it would seem the 'everything is a file' quest isnt completed yet, or at least has limitations.
> 
```
int main(int argc, char **argv)
```
argc = argument count
argv = argument value
Why is it necessary to list them here, as main doesn't have any parameters per-say? 
What does the double star in front of argv denote?

Thanks again for your help.
its habit more than anything (or a template)
re the double star, another way of writing it is char *argv[] so i would guess its because an array is a pointer.

---

### Post by fct on 2009-10-27
> **benj1 said:**
> yes its essentially your first example except treating the printer as a pipe rather than a file, im not sure why you have to do it like this, everything is supposed to be a file, it would seem the 'everything is a file' quest isnt completed yet, or at least has limitations.

The popen() function uses the path to an executable, plus arguments, to launch it and returns a pipe for inter-process communication. Even if I named it "printer" it could be any name, like the more adequate "pipe_to_lpr".

[quote=benj1]its habit more than anything (or a template)
re the double star, another way of writing it is char *argv[] so i would guess its because an array is a pointer.[/QUOTE]

It's habit, and avoids a warning when you declare main as returning void (which goes against some standards).

---

### Post by Jim_in_Germany on 2009-10-27
Thanks for the explanations. That makes things a lot clearer.
It's certainly an interesting experience learning C.
Thanks again for all the answers.

---

### Post by benj1 on 2009-10-27
> **fct said:**
> The popen() function uses the path to an executable, plus arguments.

doh, should actually read the command its running :)

have you tried sending a postscript file to the printer? maybe your printer doesnt accept plain text.

---

### Post by Jim_in_Germany on 2009-10-28
> have you tried sending a postscript file to the printer? maybe your printer doesnt accept plain text. 
No, that's cool. I'm happy with how it's working now.

I actually came up with a different solution in ruby. If you create a pair of pipe endpoints using IO.pipe, then create a fork, then in the child process shut stdin and reopen it straight away, stdin is pointing to the end of the pipe. Then using exec you can just point everything that comes from the parent process to lpr.
Looks like this:
```
rd, wr = IO.pipe
if fork
  rd.close
  wr.write "Some text to be printed"
  wr.close
  Process.wait
  exit
else
  wr.close
  $stdin.reopen(rd)
  exec `which lpr`
  rd.close
end
```
Is such a thing possible in C?
It would be interesting to find out how.
Cheers.

---

