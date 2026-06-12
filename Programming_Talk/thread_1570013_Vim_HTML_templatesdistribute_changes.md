---
title: "Vim HTML templates/distribute changes"
date: 2010-09-07
forum: Programming Talk
---

### Post by jon.reeve on 2010-09-07
Hi, I'm just learning how to use vim, and I have this issue. I have a basic webpage structure (headers, footers, etc) that should be the same in all pages. Then there is content that is different for different pages. Is there a way to set up a template or something so that when I change the core structure, like the header, it gets changed in all the pages?

---

### Post by DaithiF on 2010-09-08
Hi,
typically this problem is solved by using an 'include' feature of the web language/framework being used to generate the pages, rather than by using some facility of the editor.  In other words the pages contain placeholders that are populated dynamically by the webserver at the time of the request being served.

Examples would be php's include statement, and django's templating system.

I'm inferring from your question that you're writing static html pages rather than using a dynamic language/framework.

I can't think of any particularly easy way to do what you want in an editor, whether vim or anything else ... once you've replaced the text how would you distinguish that text that may need updating from the rest of the text that remains as is.

A couple of suggestions:
1. you could look into using/learning a framework ... in particular if the include feature is the only thing you need, you could convert your pages to php as-is and chop out the common pieces into include()s in just a few minutes.

2. if you want to stick with static html, you could create your own really simple include feature with just a shell script.

so, imagine you have a directory containing your html files.  where a file might look like this now:
```
<html>
<head>
<title>blah</title>
</head>
<body>
<div>
some common header stuff
</div>
some page-specific stuff
etc
<div>heres the footer</div>
</body>
</html>
```

You would chop out the header / footer bits into their own files header.htm and footer.htm, and replace with some placeholder text, e.g.:
```
#include header.htm
some page-specific stuff
etc
</div>
#include footer.htm

```

then running this bash script would 'build' the pages, replacing the include tags with the actual content, and writing the resulting files into a separate directory
```
#!/bin/bash

# create build directory if it does not already exist
[[ ! -e build ]] && mkdir build

# for every htm file, replace include tags with the contents of those files
for file in *.htm
do
    sed "/^#include header.htm$/{s///;r header.htm
        };
        /^#include footer.htm$/{s///;r footer.htm
        };
        /^#include other.htm$/{s///;r other.htm
        };
    " "$file" > build/"$file"
done

```

good luck

---

### Post by jon.reeve on 2010-09-29
That's so awesome, thanks.

---

