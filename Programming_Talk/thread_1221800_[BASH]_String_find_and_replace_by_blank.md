---
title: "[BASH] String find and replace by blank"
date: 2009-07-24
forum: Programming Talk
---

### Post by Martin H. on 2009-07-24
Hi all,


i am currently trying to adapt a Bash - Script that makes extensive usage 
of arrays and the 'foreach' keyword to correctly threat blanks in file - and foldernames.

I decided to replace all blanks by some special characters before putting them into the 
arrays, run foreach, and then undo the replacement to correcly handle the file/folder structure. 

While step 1 was rather quickly done im facing trouble with putting the blanks back in...

Here is what im currently doing :

```

#!/bin/bash

Org="Original searchstring !"
RepBy="_**_"
RepPatt=" "

RepOrg="${Org//$RepPatt/$RepBy}"
/bin/echo $RepOrg

```This works as expected and replaces all blanks in the Original string.

But vice versa :

```


RepPatt="_**_"
RepBy=" "

Org="${RepOrg//$RepPatt/$RepBy}"


```seems to be replacing only the first occurence and cuts out the middle of the string :confused:...

Is there a quick solution to do this, or do i have to get in touch with 'sed' ?

Thx alot,
Martin

---

### Post by ahmatti on 2009-07-24
I've done a similar script using sed in the past so at least it can fix your problem. Sorry to say that I don't the script with me, but just look from the man page how to make a global replace ina string.

---

### Post by Martin H. on 2009-07-24
Thx for your answer !


Found this solution :

```

Org=$RepOrg | sed '/s/RepPatt/RepBy/g' 
/bin/echo $Org

```sed's Variable notation is different - don't use $ !

---

### Post by benj1 on 2009-07-24
you could use

tr -d " "

or

tr " " "_"

etc

---

### Post by Martin H. on 2009-07-24
> **benj1 said:**
> you could use

tr -d " "

or

tr " " "_"

etc

Yes,

```

Org=$RepOrg | tr -s "$RepBy" "$RepPatt" 

```in this case works as well !

---

