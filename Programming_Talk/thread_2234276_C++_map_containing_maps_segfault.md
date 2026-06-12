---
title: "C++ map containing maps segfault"
date: 2014-07-13
forum: Programming Talk
---

### Post by shadesofoctober on 2014-07-13
So I wrote a small 2D engine with Allegro5 a bit ago. I decided very recently to switch to SDL2, and actually got almost everything functional again with the new API.
However, I am no longer able to rely on ALLEGRO_CONFIG for INI configuration file parsing, so I've been trying to rewrite my ConfigReader class from scratch, if just as much to learn how to anyways.

Reading a straight text file with key=value pairs was easy, with several examples to be found. I was working with a file read example I found from Alex Dantas. But I've been trying to also add in sections, like in standard INI files.

The only way I could think of doing that was an outer map containing a pair of each section associated with another map containing the key/value pairs.

```

[COLOR=#808000]typedef [/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]map[/COLOR][COLOR=#000000]<[/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]string[/COLOR][COLOR=#000000], [/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]string[/COLOR][COLOR=#000000]> [/COLOR][COLOR=#800080]innerMap[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]map[/COLOR][COLOR=#000000]<[/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]string[/COLOR][COLOR=#000000], [/COLOR][COLOR=#800080]innerMap[/COLOR][COLOR=#000000]*> [/COLOR][COLOR=#800000]config[/COLOR][COLOR=#000000];
[/COLOR]
```

My pointer knowledge is pretty pathetic.. I took me all night to figure out to get the pairs inserted into the map without compile errors. Then, when I think maybe I got it... it segfaults as soon as I attempt to do any operations with the innerMap! Here is the function to load the file.

```

[COLOR=#808000]bool [/COLOR][COLOR=#800080]ConfigReader[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#000000]loadConfig[/COLOR][COLOR=#000000]([/COLOR][COLOR=#808000]const [/COLOR][COLOR=#808000]char[/COLOR][COLOR=#000000]* [/COLOR][COLOR=#000000]filename[/COLOR][COLOR=#000000]) [/COLOR][COLOR=#000000]{
[/COLOR][COLOR=#800080] Logger[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#000000]getInstance[/COLOR][COLOR=#000000]()->[/COLOR][COLOR=#000000]logMessage[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000080]0[/COLOR][COLOR=#000000], [/COLOR][COLOR=#008000]"ConfigReader [/COLOR][COLOR=#008000]loading [/COLOR][COLOR=#008000]config [/COLOR][COLOR=#008000]file: [/COLOR][COLOR=#008000]'%s'"[/COLOR][COLOR=#000000], [/COLOR][COLOR=#000000]filename[/COLOR][COLOR=#000000]);[/COLOR]
[COLOR=#800080] 
 std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]ifstream [/COLOR][COLOR=#000000]file[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]filename[/COLOR][COLOR=#000000]);
[/COLOR][COLOR=#808000] 
 if [/COLOR][COLOR=#000000](![/COLOR][COLOR=#000000]file[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]is_open[/COLOR][COLOR=#000000]()) [/COLOR][COLOR=#000000]{
[/COLOR][COLOR=#800080]  Logger[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#000000]getInstance[/COLOR][COLOR=#000000]()->[/COLOR][COLOR=#000000]logError[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000080]0[/COLOR][COLOR=#000000], [/COLOR][COLOR=#008000]"ConfigReader [/COLOR][COLOR=#008000]failed [/COLOR][COLOR=#008000]to [/COLOR][COLOR=#008000]load [/COLOR][COLOR=#008000]config [/COLOR][COLOR=#008000]file: [/COLOR][COLOR=#008000]'%s'"[/COLOR][COLOR=#000000], [/COLOR][COLOR=#000000]filename[/COLOR][COLOR=#000000]);
[/COLOR][COLOR=#808000]  return [/COLOR][COLOR=#808000]false[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#000000] }
[/COLOR]
[COLOR=#808000] bool [/COLOR][COLOR=#000000]inSection [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#808000]false[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#800080] innerMap[/COLOR][COLOR=#000000]* [/COLOR][COLOR=#000000]iMap[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#808000]
 while [/COLOR][COLOR=#000000](![/COLOR][COLOR=#000000]file[/COLOR][COLOR=#000000].[/COLOR]eof[COLOR=#000000]()) [/COLOR][COLOR=#000000]{[/COLOR]
[COLOR=#800080]  std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]string [/COLOR][COLOR=#000000]line[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#800080]  std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#000000]getline[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]file[/COLOR][COLOR=#000000], [/COLOR][COLOR=#000000]line[/COLOR][COLOR=#000000], [/COLOR][COLOR=#008000]'\n'[/COLOR][COLOR=#000000]);[/COLOR]
[COLOR=#808000]  if [/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]line[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]empty[/COLOR][COLOR=#000000]()) [/COLOR][COLOR=#000000]{
[/COLOR][COLOR=#808000]   continue[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#000000]  }[/COLOR]
[COLOR=#808000]
  if [/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]line[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000080]0[/COLOR][COLOR=#000000]] [/COLOR][COLOR=#000000]== [/COLOR][COLOR=#000080]COMMENT_CHAR[/COLOR][COLOR=#000000]) [/COLOR][COLOR=#000000]{
[/COLOR][COLOR=#808000]   continue[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#000000]  }[/COLOR]
[COLOR=#808000]
  if [/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]line[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000080]0[/COLOR][COLOR=#000000]] [/COLOR][COLOR=#000000]== [/COLOR][COLOR=#000080]SECTION_BEGIN_CHAR[/COLOR][COLOR=#000000]) [/COLOR][COLOR=#000000]{
[/COLOR][COLOR=#000000]   inSection [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#808000]true[/COLOR][COLOR=#000000];

[/COLOR][COLOR=#800080]   innerMap [/COLOR][COLOR=#000000]tMap[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#000000]   iMap [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#000000]&[/COLOR][COLOR=#000000]tMap[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#800080]
   std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]pair[/COLOR][COLOR=#000000]<[/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]string[/COLOR][COLOR=#000000], [/COLOR][COLOR=#800080]innerMap[/COLOR][COLOR=#000000]*> [/COLOR][COLOR=#000000]sectPair [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#000000]make_pair[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]line[/COLOR][COLOR=#000000], [/COLOR][COLOR=#000000]iMap[/COLOR][COLOR=#000000]);
[/COLOR][COLOR=#800000]   config[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]insert[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]sectPair[/COLOR][COLOR=#000000]);[/COLOR]
[COLOR=#808000]   continue[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#000000]  }
[/COLOR]
[COLOR=#800080]  std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]vector[/COLOR][COLOR=#000000]<[/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]string[/COLOR][COLOR=#000000]> [/COLOR][COLOR=#000000]current [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#800080]Utilities[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]String[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#000000]split[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]line[/COLOR][COLOR=#000000], [/COLOR][COLOR=#008000]'='[/COLOR][COLOR=#000000]);[/COLOR]
[COLOR=#808000]  if [/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]inSection[/COLOR][COLOR=#000000]) [/COLOR][COLOR=#000000]{
[/COLOR][COLOR=#800080]   std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]pair[/COLOR][COLOR=#000000]<[/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]string[/COLOR][COLOR=#000000],[/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#800080]string[/COLOR][COLOR=#000000]> [/COLOR][COLOR=#000000]keyPair [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#800080]std[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#000000]make_pair[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]current[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]front[/COLOR][COLOR=#000000](), [/COLOR][COLOR=#000000]current[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]back[/COLOR][COLOR=#000000]());
[/COLOR][COLOR=#000000]   iMap[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]insert[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]keyPair[/COLOR][COLOR=#000000]);
[/COLOR][COLOR=#000000]  }
[/COLOR][COLOR=#000000] }
[/COLOR][COLOR=#808000]return [/COLOR][COLOR=#808000]true[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#000000]}
[/COLOR]
```
(It doesn't check for existing keys or strip section brackets from section names yet)

Using any of the functions to access elements from a loaded file segfaults too. Really any time I attempt to access that innerMap. I'm sure I'm doing something totally wrong, just wouldn't mind being pointed in the right direction. Probably did the references to the inner map all wrong so I'm doing some illegal memory access deal.
And yeah, I already considered using external libraries (INI and XML/JSON/ETC). I figured I'm decently close and this is all I need, so I should get it working.
Thanks for any pointers. (Bam!)

Edit: Sigh, I can't even get it to work when I make a new sample project just to practice with maps. I get obscure operator errors or matching-function errors from inside the stl_tree header. All I want is to be able to store values in the format 'map<string, map<string, string> >' and access them later at any arbitrary element or time.

---

### Post by shadesofoctober on 2014-07-14
I did quite a bit of reading on pointers, references, and maps to see what I was doing wrong.

The problem is that I approached it all wrong. Dawned on me when I read here:
[http://stackoverflow.com/questions/10333854/how-to-handle-a-map-with-pointers](http://stackoverflow.com/questions/10333854/how-to-handle-a-map-with-pointers)

Just my guess, but the previous method had me using a map containing *pointers* to other maps when I wanted the map to hold the *actual* data structures themselves. 
When the new maps were created in that block, I'm guessing they just persisted that block, leaving the main outer map containing a pointer to a nonexistent inner map.
It would make sense that any further map operations using that pointer would certainly be illegal operations, crashing the program.

I got rid of the temporary map junk and instead had a string hold the value of the current section.
Whenever I got a new section, I created a new map and placed it directly in the outer map.

Then when I wanted to insert key pairs into that section's inner map, I just had to use the outer map's [ ] operators with the "current section" string and insert them.

```
[COLOR=#800080]innerMap [/COLOR][COLOR=#000000]newMap[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#800000]config[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]curSection[/COLOR][COLOR=#000000]] [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#000000]newMap[/COLOR][COLOR=#000000];
//Later on..[/COLOR]
[COLOR=#800000]config[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]curSection[/COLOR][COLOR=#000000]].[/COLOR]insert[COLOR=#000000]([/COLOR][COLOR=#000000]keyPair[/COLOR][COLOR=#000000]);[/COLOR]
```

End result, it works great. I've messed around with several sections and keys, and it seems to load them all without issue. And the request value functions work totally fine so far too.

I just need to clean up the class, strip brackets from section names, and check for existing keys, but I'll mark solved.

---

### Post by dwhitney67 on 2014-07-23
> **shadesofoctober said:**
> 
I just need to clean up the class, strip brackets from section names, and check for existing keys, but I'll mark solved.

It might be to your advantage to understand why your first approach failed, and also be provided with information regarding your second approach.

The error with your original approach (which code follows) is that you were storing the address of a local variable.  When that variable went out of scope, so did the map structure that was on the stack:
```

   innerMap tMap;
   iMap = &tMap;

   std::pair<std::string, innerMap*> sectPair = std::make_pair(line, iMap);
   config.insert(sectPair);

```

If you had allocated the (inner) map on the heap, then you would have been alright.  For example:
```

   std::pair<std::string, innerMap*> sectPair = std::make_pair(line, new innerMap);
   config.insert(sectPair)

```

As for your final solution, bear in mind that it could be costly if the (inner) map you are adding were to have values in it.  That's because you are invoking the copy-constructor for std::map when you make this call:
```

config[curSection] = newMap;

```

In conclusion, for your particular solution, your second approach is fine.  But bear in mind the risks/costs of performing shallow-copies on objects.

---

### Post by shadesofoctober on 2014-07-24
Hi dwhitney, thank you for the insight.
Looks like I have more reading to do concerning copy constructors and shallow/deep copying :(
I would mess with it right now, but I don't have the source tree with me since I'm currently wiping my computers to put them back to mainline Ubuntu.

---

