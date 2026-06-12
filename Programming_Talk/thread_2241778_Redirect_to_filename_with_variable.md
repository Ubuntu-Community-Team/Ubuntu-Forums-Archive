---
title: "Redirect to filename with variable"
date: 2014-08-28
forum: Programming Talk
---

### Post by graylinux on 2014-08-28
Hi

I have a bash/bin script in which there is a variable $path. I am trying to echo out to a filename containing the name held in $path. I have tried a dozen combinations of braces, quotes, double quotes etc etc but to no avail, the file does not get created. My latest attempt is below

echo [Desktop Entry] >  "{$}HOME/Desktop/{$}path.desktop"

That is to say, I want to write the characters  

[Desktop Entry]

into a variably named output file?

I'm trying to get to grips with BASH but I am still at the trial/error/parrot fashion stage  !  :)

thanks

---

### Post by spjackson on 2014-08-28
```

#!/bin/bash


path=fubar
echo "[Desktop Entry]" > "${HOME}/Desktop/${path}.desktop"

```

---

### Post by steeldriver on 2014-08-28
Does the $path variable actually contain a path (directories separated by slashes), or just a filename? if the former, then the intermediate directories must exist

```

echo [Desktop Entry] > "$HOME/Desktop/$path.desktop"

```

The quotes around the target location are **optional unless the path contains whitespace** but it's good to get into the habit of including them. You'd most often see quotes around the text to be echoed as well:

```

echo "[Desktop Entry]" > "$HOME/Desktop/$path.desktop"

```

You could also use single quotes around the text **but not around the target** since they cause whatever's inside them to be treated literally i.e. prevent variable expansion

```

echo '[Desktop Entry]' > "$HOME/Desktop/$path.desktop"

```

---

### Post by graylinux on 2014-08-28
Got it!

Thanks so much to you both!..... It was a combination of my /dollars/quotes/braces and, as you say, my path had a 'rogue' directory in it!

Cheers

---

