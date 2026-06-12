---
title: "[python] String Comparison"
date: 2011-03-30
forum: Programming Talk
---

### Post by Pyro.699 on 2011-03-30
Hey guys :)

So i have this language class that I (along with the help of some skilled members here) made. It has given me the ability to easily add commas to my numbers along with being able to colorize it for the terminal. Here is the code i have:
[php]
import re, locale 
class FormatString(str): 
    def __mod__(self, other): 
        if not isinstance(other, (tuple, list)):other = (other, ) 
        other = iter(other) 
        parts = self.split("%%") 
        others = [] 
        for part in parts: 
            others.append([]) 
            for ch in part: 
                if ch == "%": 
                    try:others[-1].append(other.next()) 
                    except StopIteration:raise TypeError("not enough arguments for format string") 
        try:other.next() 
        except StopIteration:pass 
        else:raise TypeError("not all arguments converted during string formatting") 
        final = [] 
        for part, other in zip(parts, others): 
            final.append([]) 
            other = iter(other) 
            literal = iter(re.split("%.*?[a-zA-Z]", part)) 
            marker = iter(re.findall("%.*?[a-zA-Z]", part)) 
            try: 
                while 1: 
                    final[-1].append(literal.next()) 
                    m = marker.next() 
                    o = other.next() 
                    if m.startswith("%,") and m[-1] in ("i", "f"):final[-1].append(locale.format("%" + m[2:], o, grouping=True)) 
                    else:final[-1].append(m % o) 
            except StopIteration:pass 
            final[-1] = "".join(final[-1]) 
        final = "%".join(final)         
        return final
         
         
def StyleFormat(strIn):
    ''' Colors '''
    #0 = Black        # 8 = Dark Grey
    #1 = Red        # 9 = Red
    #2 = Green        #10 = Green
    #3 = Gold        #11 = Yellow
    #4 = Navy        #12 = Blue
    #5 = Magenta    #13 = Purple
    #6 = Cyan        #14 = Teal
    #7 = Grey        #15 = White
    ''' End '''
    
    ##Color
    strOut = re.sub("\{fg:(\d{1,3})\}", "\x1B[38;5;\\1m", strIn)
    strOut = re.sub("\{bg:(\d{1,3})\}", "\x1B[48;5;\\1m", strOut)
    strOut = re.sub("\{iv\}(.*?)\{/iv\}", "\x1B[7m\\1\x1B[27m", strOut) #Inverse
    
    ##Style
    strOut = re.sub("\{u\}(.*?)\{/u\}", "\x1B[4m\\1\x1B[24m", strOut) #Underline
    strOut = re.sub("\{s\}(.*?)\{/s\}", "\x1B[9m\\1\x1B[29m", strOut) #Strike-out
    strOut = re.sub("\{b\}(.*?)\{/b\}", "\x1B[1m\\1\x1B[21m", strOut) #Bold&Bright
    
    return strOut + "\x1B[0m" 
         
class LanguageMeta(type): 
    def __new__(meta, classname, bases, _dict): 
        newdict = {} 
        for key, val in _dict.iteritems(): 
            if isinstance(val, str):
                nval = StyleFormat(val)
                nval = FormatString(nval) 
                
                newdict[key] = nval
            else: 
                newdict[key] = val 
        return type.__new__(meta, classname, bases, newdict)
         
class Language(object): 
    locale.setlocale(locale.LC_ALL, '') 
    __metaclass__ = LanguageMeta 
 
#################################### 
#####Start The Actual Languages##### 
#################################### 
class _english(Language): 
    example_a = "This is an example: %,i"
    example_b = "{fg:4}This is also {bg:9}an example :)"
[/php]

Then when i wish to use something from this language class i can call *_english.example_a % 10000* or *_english.example_b* and it will print to the screen.

Now throughout the runtime of the program i log certain actions that take place via this language class. Stuff happens; it reads/writes from a log-file, conversions take place and so-on. Every day at midnight i send my self a summary email that contains all of the information in the given day. I send the email off in html format giving me the ability to highlight certain lines and add pretty fonts and colors.

What im looking for some help in is when it comes time to identify which lines get highlighted, how do i ask the simple question "does this log entry originate from this language template" (ex: **if "This is an example: 10,000" matches _english.example_a**). Also keep in mind the example i gave is quite simplified compared to some of the real templates i have.

Currently what ive done is surrounded all of the % variables in brackets [ & ] then when i want to compare i just go **if re.findall( re.sub("\[.*?\]", ".*?", _english.example_a), log_line)** and run that on every line. I personally feel this is a retarded way to do it and is bad practice. There has to be a better way to do this.

This also means that im not able to implement my the color into my templates yet because it would throw off the matcher i gave in the last paragraph...

Anyways, this is probably more than enough information.
Thanks a ton
~Cody Woolaver

---

### Post by DaithiF on 2011-03-30
when outputting the formatted strings, can you pre-pend a tag that you can use later to identify the language class it came from:
[_english]This is an example: 10,000

easy enough to strip off the tag when you only want to see the output text.

---

### Post by Pyro.699 on 2011-03-30
I had thought of that idea. but id like to avoid that if at all possible. Especially when these values will be written to files and then read from files...

---

### Post by DaithiF on 2011-03-30
ok, store the strings / classes they came from in a dict (key = string, value = the language class) and pickle it to a file which you can later read to do lookups when processing the output.

---

