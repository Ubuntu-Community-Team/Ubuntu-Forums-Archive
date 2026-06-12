---
title: "Is there a C function to &quot;split up&quot; ARGV[0]?"
date: 2009-02-20
forum: Programming Talk
---

### Post by Krupski on 2009-02-20
Hi all,

Sorry for the barrage of questions...

[COLOR="Red"]**[NOTE: This is not homework and I am not a student.]**[/COLOR]

Simple one I hope: Is there a C function that will split or parse pieces out of ARGV[0]?

What I want to do is extract just a filename from a complete path.

For example, if I execute "/usr/local/sbin/program", the contents of argv[0] will be "/usr/local/sbin/program" but what I want is to just isolate the filename itself (i.e. "program").

What I want it for is to place the actual program name into a printed help string, for example:

```

(I want this):
usage: program file1 file2

(I don't want it to do this):
usage: /usr/local/sbin/program file1 file2


```

Now, I can easily scan argv[0] backwards, copy it to a temp buffer and stop at the first "/", but why bother if there's already a standard function which does this?

Thanks in advance for any help!

-- Roger

---

### Post by monkeyking on 2009-02-20
I would tokenize it with the '/'

---

### Post by tom66 on 2009-02-20
I think the header file has 'libgen.h', which has a basename function, but I can't be sure. Here is a page I found on it: [http://www.opengroup.org/onlinepubs/009695399/basedefs/libgen.h.html](http://www.opengroup.org/onlinepubs/009695399/basedefs/libgen.h.html)

It apparently exists in gnulib.

---

### Post by hastur on 2009-02-20
hi,

in the gnu C library you have the function "basename()" which does the job.
"dirname()" obviously does the counterpart.

---

### Post by Krupski on 2009-02-20
**[COLOR="Blue"]Thank you[/COLOR]** to **tom66** and **hastur**. That's what I was looking for! [IMG]http://www.gunsnet.net/forums/images/smilies/xyxthumbs.gif[/IMG]

To **monkeyking**: What do you mean by "I would tokenize it with the '/'"?

Thanks all!

-- Roger

---

### Post by hastur on 2009-02-20
you're welcome.

I think he means use : strtok(argv[0],"/")
a useful function to split a string into token seperated by delimiters characters (although I always found the proper way to use it was difficult to grasp at first).

---

### Post by Krupski on 2009-02-20
> **hastur said:**
> you're welcome.

I think he means use : strtok(argv[0],"/")
a useful function to split a string into token seperated by delimiters characters (although I always found the proper way to use it was difficult to grasp at first).

OK I just looked up strtok(). It seems pretty straightforward. Just call it, save the pointer, then call it again until it returns null, then keep the last good pointer (which should be the end of the string... or the "basename").

In fact, that may be a nicer way to do it since I like to make my code compile in both Windows console mode and Linux... and strtok() is a standard function while basename() is not.

Thanks so much for your help!

-- Roger

---

### Post by tom66 on 2009-02-20
Keep in mind cases where Windows uses multiple directory seperators ("/" and "\"), while Linux only works with "/". The basename library should take care of this, but strtok will not unless you explicitly create a condition.

---

### Post by hastur on 2009-02-20
yup, that's about it for strtok.
still, in a common usage situation, you'd have to worry about paths like "/path/to/file" "/path//to/file///" or "/path/to/file/../", etc... strange cases should be handled easily with basename() whereas it would be longer/harder with strtok().
in your case however the simple loop should work fine. are you sure basename doesn't exists on windows ? I seem to remember the gnu doc was mentionning "different OS path schemes"...

---

### Post by Krupski on 2009-02-20
> **hastur said:**
> yup, that's about it for strtok.
still, in a common usage situation, you'd have to worry about paths like "/path/to/file" "/path//to/file///" or "/path/to/file/../", etc... strange cases should be handled easily with basename() whereas it would be longer/harder with strtok().
in your case however the simple loop should work fine. are you sure basename doesn't exists on windows ? I seem to remember the gnu doc was mentionning "different OS path schemes"...

Actually... using strtok() worked out just fine.

It took me a while to "get" exactly what it was doing, but now that I understand the code is simple. Here's what I did:

```



    char *ptr1; // pointer to previous
    char *ptr2; // pointer to current

    ptr2 = strtok(argv[0], "/"); // pointer to first "token" in argv[0]

    while(ptr2 != NULL) { // while current is not null
        ptr1 = ptr2; // copy current to previous
        ptr2 = strtok(NULL, "/"); // find next
    }

    printf("The basename is %s\n", ptr1); // debug    



```

Granted this is a TAD more complex than "basename(argv[0])", but it's portable between Linux and Windows 32 bit console mode.

Also, I have the added flexibility of using other or additional characters as delimiters (like Windows idiotic backslash).

This is cool... the more I learn the more I find there is to learn!  :)

-- Roger

---

