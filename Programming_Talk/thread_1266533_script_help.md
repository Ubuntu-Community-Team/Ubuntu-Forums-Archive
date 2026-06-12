---
title: "script help"
date: 2009-09-14
forum: Programming Talk
---

### Post by Neon612 on 2009-09-14
Is there away to have a string inside of a bash script that will be put into a gedit document?

IE:
```

HelloWorld="This is a String"
gedit Test < $HelloWorld

```

I know that doesn't work but I'm looking for a way to put ***HelloWorld*** into a newly opened gedit file "Test" in this case.

Thank you.

---

### Post by Sub101 on 2009-09-14
Could just do something like:

```

touch yourfilename
echo "your text">>$yourfilename
```

Or is there a reason you specifically want gedit?

---

### Post by Neon612 on 2009-09-14
I'd like to use gedit if possible. This script is just to set up a header for my programming class (Intro to Java), so I don't have to type the same thing over and over and over.....& no copy and paste.

I have the script set up: ./java.sh NameOfProgram

It opens gedit with file, NameOfProgram.java. And if I can get everything to work right, my header and if possible, the basics for a java program.

---

### Post by linkmaster03 on 2009-09-14
java.sh
```

#!/bin/bash
echo -e "//Java stuff\n//More java stuff" > $1
gedit $1
```

./java.sh <filename>

What is happening here is you are using echo to create and insert text into the file (-e allows \n to be translated into actual newlines), and gedit to open that file.

---

### Post by falconindy on 2009-09-14
Are you using the 'gedit-plugins' package? Why not make a snippet for the basic layout of a java .class file?

---

### Post by geirha on 2009-09-15
Alternatively use a here-doc, which is better suited than echo for multiple lines.

```

#!/bin/bash
# Print usage and exit if not invoked right
(( $# == 1 )) || { echo "Usage: $0 ClassName"; exit; } 

# Just open it if the file already exists
[[ -f "$1.java" ]] && exec gedit "$1.java"  

cat > "$1.java" << EOF
import java.util.*;

public class $1
{

}
EOF

exec gedit "$1.java"

```

---

### Post by Can+~ on 2009-09-15
Here's a far simpler thing:

[LIST=1]
[*]Write a basic Java snippet and name it "base.java".
[*]Throw it inside the ~/Templates folder.
[*]Right Click and select "Create Document" > "base.java".
[*]???????
[*]PROFIT!
[/LIST]

---

### Post by Mirge on 2009-09-15
> **Can+~ said:**
> Here's a far simpler thing:

[LIST=1]
[*]Write a basic Java snippet and name it "base.java".
[*]Throw it inside the ~/Templates folder.
[*]Right Click and select "Create Document" > "base.java".
[*]???????
[*]PROFIT!
[/LIST]


:lolflag:

---

