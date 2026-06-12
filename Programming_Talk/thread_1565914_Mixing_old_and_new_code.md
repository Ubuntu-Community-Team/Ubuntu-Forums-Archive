---
title: "Mixing old and new code"
date: 2010-09-01
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-01
Writing a config file processor, I had some old C code, but I want to give it a nice shiny contemporary interface.

Now the interface I want will be an STL map template or maybe a hash_map... not sure of the advantages yet. So you use a textual key to lookup your config parameter in the map.

The old C code would find the size of the config file, then read the whole thing into memory in one big read operation.
Then it compacts the data by stripping out the comments and redundant white space as well as null terminating all the individual strings before using realloc to reduce the amount of memory it required.

Now a modern application would expect all this text to be converted into objects of the string class and then use dynamic memory management to store them all... but then I wondered what does all that achieve? I already have all the null terminated strings in memory and storing them any other way is only going to be less eficient... so I'm really tempted to just make a hash_map of char *'s pointing to the original C strings in the compacted file buffer...

Would be interested in opinions of how to do it properly.

---

### Post by garyedwardjohnston on 2010-09-01
this is the absolute beginners forum...lol

---

### Post by worksofcraft on 2010-09-01
> **garyedwardjohnston said:**
> this is the absolute beginners forum...lol

Are beginners not also quite happy to discuss benefits of  dynamic memory allocation and garbage collection and using high level language features like string classes and containers... versus dumb old character pointers into a flipping big array in memory?
:popcorn:

p.s. I spent about 10 years programming computers... and then I quit and spent 15 years doing totally different things... and now I decided to have another look at computer programming, but this time I want to contribute to teh free software philosophy instead of running in the Microsoft treadmill ;)

---

### Post by worksofcraft on 2010-09-02
Anyway... so I have a configuration file for my kewl new application... and in there is it says something like:
```

# System standard paths
locale=/usr/share/locale # localization happens here

```

and in my application I want to call say bindtextdomain()and give it that correct path right?! Meh.. let's just print it... so, given my config file is called /etc/etc.etc:

```

	etc_obj ETC("/etc/etc.etc");
	printf("LOCALE = %s\n", (const char *) ETC["LOCALE"]);

// then in my output I get:
LOCALE = /usr/share/locale

```

The main thing is I didn't have to "new" or "delete" anything and no Garbage collector is expected to come find all my fragments of strings that I created... they are all perfectly safe without any reference counters, or whatevah until my ETC object goes out of scope! Once I leave the zone where ETC exists... well all what it read in is disposed of to free memory so all I have to do is make sure it stays in scope until I did what I wanted to with it's data.

I just wonder why that wouldn't be good enough for programmers today ?

---

