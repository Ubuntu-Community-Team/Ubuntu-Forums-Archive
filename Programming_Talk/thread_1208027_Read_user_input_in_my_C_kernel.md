---
title: "Read user input in my C kernel"
date: 2009-07-08
forum: Programming Talk
---

### Post by 2words4uready on 2009-07-08
Im wanting to read input in my C kernel and not just print out characters. Here is my current code so far. I can print out strings and clear the screen.
```
void clear_screen(char clear_to, char attrib)
{
  char *text_video = (char*)0xB8000;
  int pos=0;

  while(pos<(80*25*2))
  {
    *text_video = clear_to;
    *text_video++;
    *text_video = attrib;
    pos++;
  }
}
void WriteText(char *str,char attrib)
{
	  int num;
  char ch;

  char *text_video = (char*)0xB8000;

  while(*str!=0)
  {
    *text_video = *str;
    *text_video++;
    *text_video = attrib;
    *text_video++;
    *str++;
  }
  return;
}
void kmain( )
{
  clear_screen(0,0x02);
  WriteText("The BCS kernel has been loaded!",0x02);
  return;
  
}
```

So how do I get input form the keyboard?

---

### Post by lisati on 2009-07-16
I'd advise caution about assuming that the screen is in 80x25 mode - not all machines are the same. What if the person running your code tries it on a system which defaults to a non-standard setting?

I'm a bit hesitant to offer specific thoughts on checking the current video mode/hardware address or reading the keyboard - the last time I did anything like that was on an MS-DOS system, and the code I used also checked that the video memory was actually on the now-reasonably-standard address you've used - one of my now-trashed machines had a video card with video ram at 0xB0000

---

### Post by JordyD on 2009-07-16
Look at the [Linux kernel]("http://kernel.org/"), maybe you can get more information in there.

Considering the number of kernels around, I'd say that the number of people who know how to write a kernel around here is next to none. Although you might have some luck here with C-specific problems, problems relating to the kernel you're writing would probably be best directed at the Linux kernel itself.

I've also heard of a community that's all about writing OSes, so you might have some luck there.

Good luck.

---

### Post by soltanis on 2009-07-16
I also echo the sentiment that almost no one here has written their own kernel, so we perhaps don't have much in the way of assistance for you.

If your system is running with BIOS interrupts (is that the word for it? Where the BIOS is doing all the interfacing for you) enabled, then there should be a way to call on it to get keyboard input.

Otherwise, you need to start writing input drivers.

---

