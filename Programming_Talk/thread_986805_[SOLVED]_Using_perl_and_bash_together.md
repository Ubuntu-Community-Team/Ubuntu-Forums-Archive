---
title: "[SOLVED] Using perl and bash together"
date: 2008-11-18
forum: Programming Talk
---

### Post by Jackp90 on 2008-11-18
I am really new to programming and i don't know a lot about many languages . . . So this is what I want to do:

I want to make a more user friendly interface for mencoder for conversion between ogv files and avi files . . . this is my program thus far and as you can see it uses both bash and perl . . . its only a rough outline of what I want:

> 
#!/usr/bin/perl -w
# Convogg 1.0
# Author: Robert
# Helped by:
use strict;
print "Enter ogg name here: \n";
my $ogg;
chomp ($ogg = <STDIN>);
print "Enter avi name here: \n";
my $avi;
chomp ($avi = <STDIN>);

#!/bin/bash
mencoder -idx $ogg -ovc lavc -oac mp3lame -o $avi 
# This is the only place that bash really makes an appearance 


---

### Post by slavik on 2008-11-18
you can do the following ;)

```

#!/usr/bin/perl -w
# Convogg 1.0
# Author: Robert
# Helped by:
use strict;
print "Enter ogg name here: \n";
my $ogg;
chomp ($ogg = <STDIN>);
print "Enter avi name here: \n";
my $avi;
chomp ($avi = <STDIN>);

`mencoder -idx $ogg -ovc lavc -oac mp3lame -o $avi`;


```

---

### Post by Jackp90 on 2008-11-27
> **slavik said:**
> you can do the following ;)

```

#!/usr/bin/perl -w
# Convogg 1.0
# Author: Robert
# Helped by:
use strict;
print "Enter ogg name here: \n";
my $ogg;
chomp ($ogg = <STDIN>);
print "Enter avi name here: \n";
my $avi;
chomp ($avi = <STDIN>);

`mencoder -idx $ogg -ovc lavc -oac mp3lame -o $avi`;


```

its still not working i get the following output

> 
robert@Laptop01:~/begperl$ convogg
Useless use of a constant in void context at /bin/convogg line 12.
Enter ogg name here: 


---

### Post by slavik on 2008-11-27
try
my $ogg = <>;
chomp $ogg;

same for the other variable.

---

### Post by Jackp90 on 2008-12-01
> **slavik said:**
> try
my $ogg = <>;
chomp $ogg;

same for the other variable.

I am still getting the same output . . . and still doesnt convert the video  . . . . any other ideas

---

### Post by ghostdog74 on 2008-12-02
just use the shell,
```

#!/bin/bash
read -p "Enter ogg name: " ogg
read -p "Enter avi name: " avi
mencoder -idx $ogg -ovc lavc -oac mp3lame -o $avi


```
make sure your mencoder is compiled with libmp3lame support.

---

### Post by Jackp90 on 2008-12-03
> **ghostdog74 said:**
> just use the shell,
```

#!/bin/bash
read -p "Enter ogg name: " ogg
read -p "Enter avi name: " avi
mencoder -idx $ogg -ovc lavc -oac mp3lame -o $avi


```
make sure your mencoder is compiled with libmp3lame support.

Thanks for the suggestion I will have to see if it works

---

