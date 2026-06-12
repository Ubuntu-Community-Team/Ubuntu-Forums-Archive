---
title: "making a script edit itself in &quot;maintenance mode&quot;"
date: 2009-11-09
forum: Programming Talk
---

### Post by kainalu on 2009-11-09
Is there a way to have a script edit itself in maintenance mode if called by a special switch on command line?

part one:

how do you make a script call itself with a certain switch? like:
script.sh --maintenance

I tried the Bash Scripting guide, but I simply dont know what to search for there

part two:

how would you allow the script to dynamically edit itself? I want to have a dialog system, that when maintenance mode in invoked, it would call up dialog with some radio buttons with the various possible switches on the buttons ( I already know how to do dialog's, I just dont know the command to write the new data back to the script's variable header ). When an option is picked, it would write that back to the variable header at the top of the script. EG:


Before:
#!/bin/bash
VARIABLE_ONE=foo
VARIABLE_TWO=bar
VARIABLE_THREE=nuf
VARIABLE_FOUR=fub
{script body here}

but when called:  script.sh --maintenance, you get:



{dialog here with radio buttons}
possiblities for VARIABLE_ONE
> foo (default)
> oof
> ofo (new selection)

After:

#!/bin/bash
VARIABLE_ONE=ofo
VARIABLE_TWO=bar
VARIABLE_THREE=nuf
VARIABLE_FOUR=fub
{script body here}




THANKS GUYS!!!

---

### Post by Arndt on 2009-11-09
> **kainalu said:**
> Is there a way to have a script edit itself in maintenance mode if called by a special switch on command line?

part one:

how do you make a script call itself with a certain switch? like:
script.sh --maintenance

I tried the Bash Scripting guide, but I simply dont know what to search for there

part two:

how would you allow the script to dynamically edit itself? I want to have a dialog system, that when maintenance mode in invoked, it would call up dialog with some radio buttons with the various possible switches on the buttons ( I already know how to do dialog's, I just dont know the command to write the new data back to the script's variable header ). When an option is picked, it would write that back to the variable header at the top of the script. EG:


Before:
#!/bin/bash
VARIABLE_ONE=foo
VARIABLE_TWO=bar
VARIABLE_THREE=nuf
VARIABLE_FOUR=fub
{script body here}

but when called:  script.sh --maintenance, you get:



{dialog here with radio buttons}
possiblities for VARIABLE_ONE
> foo (default)
> oof
> ofo (new selection)

After:

#!/bin/bash
VARIABLE_ONE=ofo
VARIABLE_TWO=bar
VARIABLE_THREE=nuf
VARIABLE_FOUR=fub
{script body here}




THANKS GUYS!!!

Editing a script while it is running is generally not a good idea. Better is to let it include a separate file with the material that may change.

---

### Post by kainalu on 2009-11-09
OK, ill do that, Ill have a file with the variables. Just out of curiosity, how would you do the maintenance switch thing, as in, add this switch and the file acts differently? also, how would I tell the script to switch out the variables in an external file, say 


script.varinfo?

I know there is a bash command to look in a file and change out a string once found, just cant remember where I saw it.

---

