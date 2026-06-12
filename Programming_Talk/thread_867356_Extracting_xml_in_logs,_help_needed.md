---
title: "Extracting xml in logs, help needed?"
date: 2008-07-22
forum: Programming Talk
---

### Post by Blackie_Chan on 2008-07-22
I'm written an script that'll sends XML files to a servlet. The servlet will do some processing and then log the response (which is XML). So there's a log file that has my xml responses. 

The response will look like:

```
<process id="1234">
    -- lines of stuff --
</process>
```

I'll like to write a shell script that'll scrape the logs and print every xml response into a seperate file of the form id.xml. So for the example above, the data in the process element will be written to a file called 1234.xml.

I know how to do this in PERL, however the unix machine doesn't have PERL installed.

How else can I do it? What other tools can I use?

Thanks in advance.

---

### Post by LaRoza on 2008-07-22
> **Blackie_Chan said:**
> 
How else can I do it? What other tools can I use?


First, what tools do you **have**?

Idealy, you'd want to use XML libraries for this, but if all you have is the standard Unix tools, you'd have to hack it with regular expressions.

---

### Post by mssever on 2008-07-22
> **Blackie_Chan said:**
> I know how to do this in PERL, however the unix machine doesn't have PERL installed.

How else can I do it? What other tools can I use?
Wow. I've never heard of a *nix machine without Perl. As LaRoza said, you can use regular expressions, but surely you have *some* option. If you don't have anything like Ruby or Python, either, you might be able to find a C XML library and write it in C.

---

### Post by scragar on 2008-07-22
> **mssever said:**
> Wow. I've never heard of a *nix machine without Perl. As LaRoza said, you can use regular expressions, but surely you have *some* option. If you don't have anything like Ruby or Python, either, you might be able to find a C XML library and write it in C.

perl didn't come with dapper, I had to install that myself when I wanted to start learning it.

---

### Post by Blackie_Chan on 2008-07-22
> **mssever said:**
> Wow. I've never heard of a *nix machine without Perl. As LaRoza said, you can use regular expressions, but surely you have *some* option. If you don't have anything like Ruby or Python, either, you might be able to find a C XML library and write it in C.

I don't think the machine has Ruby or Python (given it doesn't have Perl, I'll check tommorow at work). Isn't it possible use unix tools? grep, sed, awk and so on?

---

### Post by ghostdog74 on 2008-07-22
Surely, without those languages, you can still survive, at least for your case. The granddaddy of Perl
```

awk 'BEGIN{FS="[>=]"}
/<process id/{ gsub("\"",""); id=$2;f=1;next}
/<\/process>/{f=0;next}
f{print $0 > id".xml"}' file

```

---

### Post by mssever on 2008-07-22
> **Blackie_Chan said:**
> \Isn't it possible use unix tools? grep, sed, awk and so on?

It's possible, but having an XML library would make for much cleaner code than doing it via regex. And with sed and grep, regular expressions are all that's available. I don't know awk, so I can't comment on an XML library, except to note that ghostdog74's code uses regexps, not an XML library, and he's our local awk expert.

EDIT: On looking at ghostdog74's code, I'm thinking it might do what you want as written.

---

### Post by ghostdog74 on 2008-07-22
> **mssever said:**
>  I don't know awk, so I can't comment on an XML library,

(g)awk and doesn't have XML libraries. However xgawk does XML.
> 
 and he's our local awk expert.
no i am not :)

> 
EDIT: On looking at ghostdog74's code, I'm thinking it might do what you want as written.
Its possible the tags may be on one line, or jumbled. So the solution is only based on what's provided.

---

### Post by WW on 2008-07-22
> **mssever said:**
> 
EDIT: On looking at ghostdog74's code, I'm thinking it might do what you want as written.
A quick test on my Ubuntu computer shows that it works fine.  On my Mac, however, I had to change **{print $0 > id".xml"}** to **{fn=id".xml"; print $0 > fn}**.

---

### Post by LaRoza on 2008-07-23
> **Blackie_Chan said:**
> I don't think the machine has Ruby or Python (given it doesn't have Perl, I'll check tommorow at work). Isn't it possible use unix tools? grep, sed, awk and so on?

Yes. I was going to write earlier that you should wait for ghostdog74...

> **ghostdog74 said:**
> Surely, without those languages, you can still survive, at least for your case. The granddaddy of Perl


And I was too late.

> **ghostdog74 said:**
> 
no i am not :)


You're close enough ;)

---

### Post by Reiger on 2008-07-23
Well if it's clean code you want and you can feed your output to a web browser; the simple solution would be to use XSLT. :-\"

---

