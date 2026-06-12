---
title: "regular expression &quot;/^MDTM(?!\n)\s[^\n]{100}/smi&quot;"
date: 2007-02-25
forum: Programming Talk
---

### Post by Andrea_44 on 2007-02-25
I am having difficulties translating the following pcre (perl compatible regular expression).

```
pcre:"/^MDTM(?!\n)\s[^\n]{100}/smi";

```

Could anyone give an example that matches this pcre?

Any help will be greatly appreciated!

Cheers~
Andrea

FYI, The expression comes from the following FTP Snort rule:
```
alert tcp $EXTERNAL_NET any -> $HOME_NET 21 
(msg:"FTP MDTM overflow attempt"; flow:to_server,established;
content:"MDTM"; nocase; isdataat:100,relative;
pcre:"/^MDTM(?!\n)\s[^\n]{100}/smi"; 
reference:bugtraq,9751; reference:cve,2001-1021; reference:cve,2004-0330; reference:nessus,12080; classtype:attempted-admin; sid:2546; rev:6;)
```

The following describes the syntax of regular expressions
[http://perldoc.perl.org/perlre.html]("http://perldoc.perl.org/perlre.html")

---

### Post by kidders on 2007-02-25
Hi there,

This is how I would interpret it ... I *hope* it's accurate:

[LIST]
[*]/^MDTM(?!\n)\s[^\n]{100}/**[COLOR="DarkRed"]smi[/COLOR]** - "smi" looks like "Consider _all_ whitespace characters to be whitespace characters", "Multi-line mode", "Be case insensitive".
[*]/**[COLOR="DarkRed"]^MDTM[/COLOR]**(?!\n)\s[^\n]{100}/smi - The characters "MDTM" must appear at the start of a line.
[*]/^MDTM**[COLOR="DarkRed"](?!\n)[/COLOR]**\s[^\n]{100}/smi - This is a look-ahead. "MDTM" must not be followed by a line break.
[*]/^MDTM(?!\n)**[COLOR="DarkRed"]\s[^\n]{100}[/COLOR]**/smi - Next comes a single whitespace character, followed by exactly 100 characters that can be anything *except* whitespace.
[/LIST]

So, the following would match the expression:
```
MDTM 1234567890!@£$%^&*()ABCDEFGHIJ.,.,.,.,.,12345670..... (117 characters)
```

**Edit:** The idea seems to be to identify excessively long MTDM arguments, without making any attempt to match more than one argument ... or even all of a first one.

I hope that helps.

---

### Post by Andrea_44 on 2007-02-25
Thank you so much for the clear explanation:>
It helps a lot!

Cheers~
Andrea

---

