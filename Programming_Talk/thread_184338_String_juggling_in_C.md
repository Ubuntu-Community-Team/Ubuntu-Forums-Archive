---
title: "String juggling in C"
date: 2006-05-29
forum: Programming Talk
---

### Post by simplyw00x on 2006-05-29
Long story short - I'm trying to convert the string
```
Artist - Track
```to two strings:
```
Artist
Track
```but only if a third string is
```
Various Artists
```

The original string:
```
Artist - Track
```needs to handle any values for Artist and track including spaces and punctuation but it will always have _exactly_ " - " in the middle provided that the second string is "Various Artists" (again exactly).

I've been headbanging with a load of C string docs to no avail and am getting really frustrated. Any help?

---

### Post by ekarni on 2006-05-29
How about the following?  Expect a few bugs (if it works at all - I haven't done C strings or pointer arithmetic in a while) ;) 

```

char *VarArtStr = "Various Artists";  /* Or not */
char *SongLabel = "SomeArtist - SomeTrack";  
char *offset_ptr;  /*Where the " - " falls within SongLabel */

char Artist[64];  /*Strings to hold the parsed Artist and Track*/
char Track[64];   /*I'm lazy, so statically allocate*/

int SongLabelLen, Noffset;

 /*Check to see if it's Various Artists*/
if(!strcmp(VarArtStr,"Various Artists"))   /*strcmp returns 0 if the strings match*/
{
  /*Find out where the " - " is */
  offset_ptr = strstr(VarArtStr," - ");  /* strstr attempts to find string2 in string1, and returns a pointer to the base address of string2 in string1 if successful */

  /*Split out the stuff before and after the " - " */
  SongLabelLen = strlen(VarArtStr); /* Count characters in VarArtStr*/
  Noffset = offset_ptr - VarArtStr;  /*Danger, shady pointer arithmetic!!! */
 
  strncpy(Artist,SongLabel,Noffset);   /*copy Noffset characters from SongLabel to Artist strings*/
  strcpy(Track,SongLabel+Noffset+3);  /*now copy the rest of SongLabel to Track */
}

```

---

### Post by rplantz on 2006-05-29
I would probably roll my own -- something along the lines of:

```

int my_string_test(char *src, char *dest) {
   int result;
   while ((*src != '\0') && (*dest != '\0)) {
      /* body sets result as needed */
      src++;
      dest++;
   }
   return result;
}

```

---

### Post by thumper on 2006-05-30
What do you do if the Artist contains the string " - "?

Any particular reason you are doing this in C?  It screams out for perl or python.

If however it is in the middle of some other app, then strstr and strncpy are your friends.

PS. Don't bother rolling your own.  Use the string functions from the library, and you are less likely to make a mistake.

---

### Post by simplyw00x on 2006-05-30
> What do you do if the Artist contains the string " - "?
Nothing.

> Any particular reason you are doing this in C? It screams out for perl or python.
If I had my 'druthers I'd be doing it in PHP but I'm hacking up rhythmbox's notifications and that's all in C.

> If however it is in the middle of some other app, then strstr and strncpy are your friends.
Is there a good reason that C's string functions are so thin on the ground and complicated? I spent an hour and a half yesterday trying to find out how to cut a string. I still don't know.

> How about the following? Expect a few bugs (if it works at all - I haven't done C strings or pointer arithmetic in a while)  
You may have just saved me another migrane. Many thanks.

> I would probably roll my own -- something along the lines of:
It only needs to be used once; no need for a function. Thanks anyway.



I'm really impressed with the feedback; I thought the programming subforum was a bit of a ghost town up 'til now. Thanks to all.

---

### Post by thumper on 2006-05-30
[QUOTE=simplyw00x]Is there a good reason that C's string functions are so thin on the ground and complicated? I spent an hour and a half yesterday trying to find out how to cut a string. I still don't know.[/QUOTE]
C deals with low level stuff.  What do you mean by cutting a string?

There are a couple of ways of shortening a string...
A common way is just to insert the string terminator character (zero, or \0) after the last character you care about.  strlen counts characters to the null terminator, strcpy copies to the null terminator, so effectively the string is now shorter.

It is a common idiom to allocate memory for the string you need (making sure to free them too), or to use fixed size buffers as above.  Using static fixed size buffers is a problem if the functions need to be re-entrant.

[QUOTE=simplyw00x]I'm really impressed with the feedback; I thought the programming subforum was a bit of a ghost town up 'til now. Thanks to all.[/QUOTE]
Nah, there are quite a few of us here that like helping out.

---

### Post by simplyw00x on 2006-05-30
> A common way is just to insert the string terminator character (zero, or \0) after the last character you care about. strlen counts characters to the null terminator, strcpy copies to the null terminator, so effectively the string is now shorter.
That seems pretty easy; I'm used to higher-level things like PHP, Java and... *chortle*... C++

I manage to shoehorn in ekarni's code (a couple of typos :p) and it works fine in my test program ([here]("http://pastebin.com/746606")) but when I whack it into RB ([here]("http://pastebin.com/746604")) it gives me mystery segfaults and silent crashes ([here]("http://pastebin.com/746639")). I _hate_ memory management...

If you could possibly see any glaring n00b errors I'd really appreciate it. Thanks.

---

### Post by thumper on 2006-05-30
```
if(!strcmp(song.artist,"Various Artists"))
{
  g_warning ("Sending notification (%s)", song.title);
  /*Find out where the " - " is */
  offset_ptr = strstr(song.title," - "); 
  if(offset_ptr == NULL) 
  {
    /* give yourself an out here. */
    /* assigning to "NULL" is asking for a world of hurt */
    notifytitle = g_strdup_printf(_("%s"), song.title);
  }
  else 
  {
    /*Split out the stuff before and after the " - " */
    SongLabelLen = strlen(song.title);
    Noffset = offset_ptr - song.title;
    
    /* strncpy does not null terminate the string */
    strncpy(Artist, song.title, Noffset);
    Artist[Noffset] = 0; /* add the terminator */
    /* strcpy does copy the null terminator */
    strcpy(Track, offset_ptr + 3);
    notifytitle = g_strdup_printf (_("%s by %s"), Track, Artist);
  }
}
```
The main point is that **strncpy** does not null terminate the string.

---

### Post by simplyw00x on 2006-05-30
> The main point is that strncpy does not null terminate the string.
I see... damn me not reading the doc pages properly. Thanks!

Apparently (at least according to [http://www.space.unibe.ch/comp_doc/c_manual/C/EXAMPLES/strncpy.c](http://www.space.unibe.ch/comp_doc/c_manual/C/EXAMPLES/strncpy.c)) I should have ```
Artist[sizeof(Artist)-1] = '\0';
```
instead of ```
Artist[Noffset] = 0;
```

That look right?

---

### Post by thumper on 2006-05-30
sizeof(Artist) will return the size of the character buffer (64).

Noffset is the offset into the song title string giving the position of the start of the " - " separator string.

If the separator is at position 23, then you want the null terminator there, not at index 63.  Does that make sense to you?

---

### Post by simplyw00x on 2006-05-30
That makes perfect sense. Is there any way of debugging these things myself? Like printing whether or not a string is null-terminated? Or gdb? It sucks having to rely on other people's goodwill for my own personal project.

---

### Post by thumper on 2006-05-30
You could always check the length of the string using **strlen** as it stops at the first null.

Passing **char*** values to functions when you don't know if they are terminated or not when they are expected to be is just asking for trouble.

Best thing is to "do the right thing" (TM), and make sure you terminte your strings if the function call doesn't :)

---

### Post by rplantz on 2006-05-31
[QUOTE=thumper]You could always check the length of the string using **strlen** as it stops at the first null.
[/quote]
And I always forget if **strlen** includes the NUL character since I don't use it very often.
> 
Passing **char*** values to functions when you don't know if they are terminated or not when they are expected to be is just asking for trouble.

One of the biggest dangers here is that sometimes there just happens to be a NUL after your string, other times not. Behavior appears to be random.
> 
Best thing is to "do the right thing" (TM), and make sure you terminte your strings if the function call doesn't :)
This is why I prefer to roll my own. The standard C functions for handling text strings seem to have too many inconsistencies. If I used them a lot, I would learn their foibles. But for an occassional application, I find it easier to simply do it myself. Then I know how it works.

---

### Post by ynef on 2006-06-01
[QUOTE=simplyw00x]Is there a good reason that C's string functions are so thin on the ground and complicated? I spent an hour and a half yesterday trying to find out how to cut a string. I still don't know.[/QUOTE]
If this means what I think it does, you should look up how to use the "strtok" function. It tokenizes a string, which means that it splits it up into smaller chunks (tokens). For instance, you could tell the strtok function to split at " - ", and you'd get the Artist part as the first token and the Track as the second.

---

### Post by thumper on 2006-06-01
strtok is evil.

It uses global variables to store state.  Not too much of a problem if you are writing noddy programs or you know for sure that you are only ever in a single threaded environment, otherwise stay well away.

---

### Post by simplyw00x on 2006-06-01
> strtok is evil.
Having tried to use it, and looked at the examples - yes it is.

A quick progress update - I managed to get this working in the end; now my RB notifications show "Track - Artist" instead of "Various Artists - Artist - Track". Still working on have the MusicBrainz notification sent out in that form as well (the original purpose) but this is a step forward. Thanks guys!

---

### Post by rplantz on 2006-06-01
[QUOTE=thumper]strtok is evil.

It uses global variables to store state.  Not too much of a problem if you are writing noddy programs or you know for sure that you are only ever in a single threaded environment, otherwise stay well away.[/QUOTE]

There is also strtok_r, the reentrant version. You supply a char ** variable for storing the state in your own space.

I think somebody remarked about using standard functions to avoid having to deal with C pointers. I'll leave it to the reader to decide whether dealing with char ** is easier than rolling your own. :)

I've written a lot of code over the past 40 years. I would guess that the majority of my time has been spent dealing with text strings. Just when you think you have it nailed, some naive user manages to invent a new keystroke combination. It's great fun. :)

---

### Post by LordHunter317 on 2006-06-01
Don't use any version of strtok.  Just don't.

strsep() is somewhat better, but still evil.  Write your own.

And, it's important where you can, to use safe version of the string functions: strlcpy, strlcat, etc. written by OpenBSD.  They can be a portability issue, however.

---

### Post by rplantz on 2006-06-01
[QUOTE=LordHunter317]Don't use any version of strtok.  Just don't.

strsep() is somewhat better, but still evil.  Write your own.
[/QUOTE]

LordHunter317, can you give a better reason than "evil"?

Please understand that I am not trying to argue with you, but I really would like to know for my own education. I understand that strtok is not thread safe. But is there a bug in strtok_r?

By the way, I do know that some software is not perfect. For example, I worked with rsync on my Mac OS X. There are several versions, all of which have some problems. But when I see warnings about using software, I like to know why. (Recall that I'm one who has advocated rolling your own a couple of times in this thread.)

---

### Post by LordHunter317 on 2006-06-01
[QUOTE=rplantz]LordHunter317, can you give a better reason than "evil"?[/quote]It has all the same problems strtok() has: it destroys the source string, it's handling of tokens is illogical (if not flatout wrong), and it has the disadvantage of being far less portable.

That's ignoring strtok() is an obsoleted interface anyway.

>  I understand that strtok is not thread safe. But is there a bug in strtok_r?Besides the portability issues, it just has all the same problems of strtok().

---

### Post by rplantz on 2006-06-01
[QUOTE=LordHunter317].... it destroys the source string, ....[/QUOTE]

I agree. That's evil. :)

---

