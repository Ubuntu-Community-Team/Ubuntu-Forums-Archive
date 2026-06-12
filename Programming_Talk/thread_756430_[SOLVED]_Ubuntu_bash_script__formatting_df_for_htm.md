---
title: "[SOLVED] Ubuntu bash script || formatting df for html tables"
date: 2008-04-15
forum: Programming Talk
---

### Post by AKern011 on 2008-04-15
I'm working on a script for my LAMP server, which collects system data, and prints it out in a neat little html file. The file is to be available to view to see system specs etc on the internet.

Unfortunately, the format that bash outputs the data in is less than desirable. My question is:
How can I loop through a single line of terminal output and replace whitespace in the line with an XML or HTML tag. For instance, I want to display 
```

df -h

```
in a table. I can get single lines by
```

df -h | head -l 1

```
but is there anyway to separate each column header, and add a <tr> or <td> tag in between?

Thanks for any help...
Andy

---

### Post by mssever on 2008-04-15
If you're determined to use Bash, that isn't a simple solution. Here's some (untested) Ruby code. Of course, you could probably apply the same algorithm to any other sufficiently-advanced language. Some might suggest awk for this, but unless you already know awk, I don't think that it's worth learning nowadays.

```
#!/usr/bin/env ruby

df = `df -h`.chomp.split("\n")
out = ["<table>"]
df.each do |line|
  out.push('  <tr>')
  line.split(/[\s]+/).each do |col|
    out.push("    <td>#{col}</td>")
  end
  out.push('  </tr>')
end
out.push("</table>")
puts out.join("\n")
```EDIT: This code will fail if df outputs any column containing whitespace (such as a mountpoint name with spaces).

EDIT 2: Here's my example again, this time in pseudocode:
```
df = the output of df -h split into an array at every line break
out = an array containing the single string "<table>"
for each item in array as line:
    append "  <tr>" to out
    split the line on whitespace and loop over the resulting array:
        append "    <td>${The current item in the array}</td>" to out
    end loop
    append "  </tr>" to out
end loop
append "</table>" to out
join the elements in out using "\n" as the separator
```

---

### Post by WW on 2008-04-16
> **mssever said:**
> Some might suggest awk for this...

What the heck:
```

df -h | awk 'BEGIN{print("<table>")}{print("<tr><td>",$1,"</td><td>",$2,"</td><td>",$3,"</td><td>",$4,"</td><td>",$5,"</td><td>",$6,$7,"</td></tr>")}END{print("</table>")}'

```
This has the same problem with spaces in the volume names as mssever's Ruby script.  It also has a potential problem if a volume name contains < or >; I don't know if this could occur in Linux, but it is possible on a Mac.  If that is an issue, you can convert < and > to &lt; and &gt; respectively, before converting to html:
```

df -h | sed 's/</\&lt;/g; s/>/\&gt;/g' | awk 'BEGIN{print("<table>")}{print("<tr><td>",$1,"</td><td>",$2,"</td><td>",$3,"</td><td>",$4,"</td><td>",$5,"</td><td>",$6,$7,"</td></tr>")}END{print("</table>")}'

```

---

### Post by AKern011 on 2008-04-16
Thanks for the help guys. They both work well for df which is what it's meant for!

---

### Post by ghostdog74 on 2008-04-16
just another way
```

df -h | awk 'BEGIN{ print("<table border=1><tr>") }
    { 
      for ( i = 1; i<=NF ; i++ ) {   
         printf "<td> %s </td> ", $i
      }
      print "</tr>"
}
END{ 
    print("</table>")
}'

```

---

### Post by ghostdog74 on 2008-04-16
> **mssever said:**
>  Some might suggest awk for this, but unless you already know awk, I don't think that it's worth learning nowadays.

awk can do quite a lot, sometimes without using much bash (internals). Its a programming language after all. So why is it not worth learning nowadays.

---

### Post by ruy_lopez on 2008-04-16
> **ghostdog74 said:**
> just another way
```

df -h | awk 'BEGIN{ print("<table border=1><tr>") }
    { 
      for ( i = 1; i<=NF ; i++ ) {   
         printf "<td> %s </td> ", $i
      }
      print "</tr>"
}
END{ 
    print("</table>")
}'

```

If you know C, this is easy to understand. It's pretty elegant. If awk always looked this easy, I'd be inclined to take it more seriously.

---

### Post by ghostdog74 on 2008-04-16
> **ruy_lopez said:**
> If you know C, this is easy to understand. It's pretty elegant. If awk always looked this easy, I'd be inclined to take it more seriously.
it will be easy once one gets the hang of it. Same with  learning any other languages. Also, elegance is in the eye of the beholder as well as how the coder writes his code following a certain standard. Even Perl can be written elegantly.

---

### Post by WW on 2008-04-16
> **ghostdog74 said:**
> just another way
```

df -h | awk 'BEGIN{ print("<table border=1><tr>") }
    { 
      for ( i = 1; i<=NF ; i++ ) {   
         printf "<td> %s </td> ", $i
      }
      print "</tr>"
}
END{ 
    print("</table>")
}'

```
Shouldn't that first <tr> be inside the main section?
```

df -h | awk 'BEGIN{ print("<table border=1>") }
    { 
      print "<tr>"
      for ( i = 1; i<=NF ; i++ ) {
        ... etc. ...

```

---

### Post by ghostdog74 on 2008-04-16
> **WW said:**
> Shouldn't that first <tr> be inside the main section?
```

df -h | awk 'BEGIN{ print("<table border=1>") }
    { 
      print "<tr>"
      for ( i = 1; i<=NF ; i++ ) {
        ... etc. ...

```

yes, it does. good catch.

---

### Post by mssever on 2008-04-16
> **ghostdog74 said:**
> awk can do quite a lot, sometimes without using much bash (internals). Its a programming language after all. So why is it not worth learning nowadays.I figured you'd show up with an awk solution. :) awk was written to improve on shell scripting. Perl was written to improve on awk. Ruby and Python both improve on Perl. So time learning Ruby or Python is better spent; not only can those programs easily accomplish what awk can, but they have a larger problem domain, as well. Plus, awk's documentation isn't all that great to learn the language from.

I say this as someone with only the most rudimentary knowledge of awk. I don't need it.
> **ruy_lopez said:**
> If you know C, this is easy to understand. It's pretty elegant. If awk always looked this easy, I'd be inclined to take it more seriously.

Yes, ghostdog74 is the only one I've seen who writes readable awk.

---

