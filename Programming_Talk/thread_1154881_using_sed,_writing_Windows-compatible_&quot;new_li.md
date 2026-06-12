---
title: "using sed, writing Windows-compatible &quot;new line&quot;"
date: 2009-05-10
forum: Programming Talk
---

### Post by yc2 on 2009-05-10
I usually keep an Ubuntu server, but my webpage temporarily resides on GoDaddy hosting.

I use sed through php. The files that come out do not get new lines under Windows.

I can make sed recognize new lines and exchanged them for html (<br>) but how do I put real new-line-characters into the file?

I have seen the following advice but I am not sure how to apply it under php. I get the quotes wrong somehow.

```
 sed "s/$/`echo -e \\\r`/"            # command line under ksh
 sed 's/$'"/`echo \\\r`/"             # command line under bash
 sed "s/$/`echo \\\r`/"               # command line under zsh
 sed 's/$/\r/'                        # gsed 3.02.80
```

Please give me back my good night's sleep ;) and tell me how to change this line to give a text-file with new lines readable under Windows.

```
<?php
$output = shell_exec('sed -e \'s/$/<br>/\'  in.txt');
echo $output;
?>
```

---

### Post by Reiger on 2009-05-10
Or use PHP?

A quick way (skipping the sed because you don't need that):

[php]
$input  = file('in.txt'); // read the file into an array of lines
$output = implode("\r\n",$input); // concatenate all the lines with a CR+LF for line break
echo $output; // echo the result
[/php]

---

### Post by yc2 on 2009-05-10
Thanks for feedback Reiger, I am sure your advice is well founded, but the problem still persists.

I have a textfile created under Windows. I use Linux-hosting under GoDaddy. Nither sed nor implode-concatenation will keep the new line characters in the file.

At least I know the input file is OK in the way that it opens with new lines in f.ex. Notepad and when using sed, as above, s/$/<br>/, the $ will find the new lines.

Thanks Rieger, but I need more advice, please.

php version is 4.3.11

---

### Post by yc2 on 2009-05-10
I think the problem is not in sed.

I think the problem is that since I used "echo" the browser will interpret the result as html and new-line will disappear.

If I just run the output to a file and then link the browser to this text-file, it all comes out OK (with new-lines). If the browser receives a link to a textfile, it will interpret the new-line character as new-line (whereas in html it will appear as a blank).

```
$output = shell_exec('sed -e \'s/foo/bar/g\' -e \'s/\[/\{/g\' -e \'s/\]/\}/g\' in.txt > out.txt');
```

If I direct the browser to out.txt, the new-line-characters are OK.

I think this thread is solved. Sorry for putting a misleading question from the beginning.

---

### Post by Reiger on 2009-05-10
You can inform the browser that you actually send text/plain instead of text/html using the header() function in PHP [sends raw HTTP headers]. You must call header() before *any* actual output (either through PHP errors or otherwise) is sent, though.

In your case the call would look like header('Content-type: text/plain');

---

### Post by yc2 on 2009-05-10
> Reiger wrote:
header('Content-type: text/plain');
I get it, thanks.

---

