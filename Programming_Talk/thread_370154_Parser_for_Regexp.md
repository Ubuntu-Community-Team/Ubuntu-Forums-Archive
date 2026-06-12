---
title: "Parser for Regexp"
date: 2007-02-25
forum: Programming Talk
---

### Post by Andrea_44 on 2007-02-25
I am attempting to write a program to interpret PCRE (perl compatible regular expression) into literal text.

For example:
```
$./MyProgram /^MDTM(?!\n)\s[^\n]{100}/smi
```

Output:
```
MDTM 1234567890!@£$%^&*()ABCDEFGHIJaaaaaaaaaaaaaa...
```

Are there any existing program that can do this already?
or
Could you please give me some ideas on how I should approach the issues? 
i.e. Can I use "Lex"? Is it a good idea to use C or Java? What libraries should I use?

Any help will be very nice.

Thanks,
Andrea

---

### Post by nereid on 2007-02-25
Why don't you use Perl? BTW there are some web regexp parsers around. You can give them a regexp and some text and they will highlight the matched pattern.

**Edit:**
A program which parses the regexp themselves is a little bit tricky to do, which requires some serious knowledge of them. If you've got the knowledge you don't need the program anymore ;)

---

### Post by Andrea_44 on 2007-02-27
> **nereid said:**
> BTW there are some web regexp parsers around. You can give them a regexp and some text and they will highlight the matched pattern.


Thanks for the reply, but that is not quite what I meant.

What I meant was that you give my program a regexp and it will generate some text that will matched the pattern.

For example: MyProgram can parse in the Regexp below....
```
$./MyProgram /^MDTM(?!\n)\s[^\n]{100}/smi
```

And then generate the text below that will match the Regexp MyProgram has just parsed...
```
MDTM 1234567890!@£$%^&*()ABCDEFGHIJaaaaaaaaaaaaaa...
```

Is it even possible to do that?

Cheers~
Andrea

FYI, I am attempting to write a program that parse in Snort rules(containing PCRE) and generate packets (containing payload that matches the PCRE) which will trigger the Snort rules.

---

### Post by nereid on 2007-02-27
It should be possible but requires some serious thought. Which I ain't have the time for at the moment.

You should parse the regexp. Take a look at the modifiers behind them and watch out for modifiers in the regexp. Second look out for the ^ and the $. Then you'll have to model the lookahead and lookbehing modifier. And so on...This requires some heavy knowledge and in the end you'll build a compiler from regexp to plain text, which isn't easy.

---

