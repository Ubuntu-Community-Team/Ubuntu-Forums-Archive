---
title: "Bluefish: Using External Browser with spaces in Path Name"
date: 2008-01-07
forum: Programming Talk
---

### Post by Palcrypt on 2008-01-07
Ok. It was easy enough to add Firefox to my browsers in bluefish. The problem is, if I'm working with a file that has spaces in the path it won't open properly. Bluefish just cuts off the file path from the first space on. This is an issue because I'm opening some files stored on my windows partition. I'm assuming there's a command I can put in the Utilities and Filters section to parse for spaces and replace them with a percent20 or the proper linux escape sequence.

---

### Post by geirha on 2008-01-07
I assume you set a command like *firefox %s* or similar? If so, try with quotes, *firefox "%s"*

---

### Post by Palcrypt on 2008-01-07
I figured it out. I realized I was going about it the wrong way. I was putting the command in the "Utilities and Filters" section, expecting it would be applied to the file name. Instead I needed to put it all in the "Browsers" section.

So should anyone else come across this problem here's the solution. In your External Programs section of your preferences. Add firefox as a browser and put this in as the command:

```

firefox '%s' | sed 's/ /%20/g' &

```

---

