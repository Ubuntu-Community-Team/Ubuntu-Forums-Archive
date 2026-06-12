---
title: "[python] Adding Commas With % Opperator"
date: 2010-12-17
forum: Programming Talk
---

### Post by Pyro.699 on 2010-12-17
Now, I know that there are many unique ways of adding commas such as locale and recursive functions. I have looked through the library and couldn't find any conclusive answer to if this is possible to do with the % operator. I have a language file that is setup like this:[php]
class _english:
    winnings = "You have just won [ %i ] dollars"
[/php]as an example. Then when i want to call the sting i will do this:[php]
print _english.winnings % 1000
[/php]Now, is there a way that i can add commas' to that 1000 easily? Throughout the language file there are literary hundreds of areas where i want to add commas to the language file, and surrounding each instance of an integer with a special function is a bit tedious for me.

Thanks for the replies
~Cody

---

### Post by StephenF on 2010-12-18
I guess what you mean is you want a thousands separator. This code will print the correct separator for your country. It may separate on a different boundary and be a ',' or '.' character. Correct operation requires the LANG environment variable to be set appropriately.
```

import locale

locale.setlocale(locale.LC_ALL, '')
print locale.format("%i", 1234567, grouping=True)
print locale.currency(1234567, grouping=True)

```

---

### Post by Pyro.699 on 2010-12-18
> **StephenF said:**
> I guess what you mean is you want a thousands separator. This code will print the correct separator for your country. It may separate on a different boundary and be a ',' or '.' character. Correct operation requires the LANG environment variable to be set appropriately.
```

import locale

locale.setlocale(locale.LC_ALL, '')
print locale.format("%i", 1234567, grouping=True)
print locale.currency(1234567, grouping=True)

```

If you read my first post more carefully i already mentioned that i know about locale and about those ways to add a thousands separator... I'm asking if there is a way to do this in the way i mentioned...

---

### Post by StephenF on 2010-12-18
I guess this is what you need then. Note: Python 2 syntax.
```

import re
import locale


class CommaString(str):
    def __mod__(self, other):
        # Handle non tuple or list possibility for single items.
        if not isinstance(other, (tuple, list)):
            other = (other, )
        other = iter(other)
        
        # Handle %% for printing literal %.
        # Match up all our strings with their items.
        parts = self.split("%%")
        others = []
        for part in parts:
            others.append([])
            for ch in part:
                if ch == "%":
                    try:
                        others[-1].append(other.next())
                    except StopIteration:
                        raise TypeError("not enough arguments for format string")

        try:
            other.next()
        except StopIteration:
            pass
        else:
            raise TypeError("not all arguments converted during string formatting")

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
                    if m.startswith("%,") and m[-1] in ("i", "f"):
                        final[-1].append(locale.format("%" + m[2:], o, grouping=True))
                    else:
                        final[-1].append(m % o)
            except StopIteration:
                pass

            final[-1] = "".join(final[-1])
            
        # The %% characters go back in as literal %.    
        final = "%".join(final)
        
        return final


class LanguageMeta(type):
    """Metaclass to change instances of str to CommaString."""
    
    def __new__(meta, classname, bases, _dict):
        newdict = {}
        for key, val in _dict.iteritems():
            if isinstance(val, str) and "%," in val:
                val = CommaString(val)
            newdict[key] = val   
        
        return type.__new__(meta, classname, bases, newdict)


class Language(object):
    """Base class for language classes."""
    
    __metaclass__ = LanguageMeta


class _english(Language):
    winnings = "You have won %,i dollars, %s...  show literal percent %% ok done"


if __name__ == "__main__":
    # Example usage.
    
    locale.setlocale(locale.LC_ALL, '')
    print _english.winnings % (1000000, "Sidney")

```
Example output
```

You have won 1,000,000 dollars, Sidney...  show literal percent % ok done

```

---

### Post by Pyro.699 on 2010-12-18
...

I'm speechless... this is EXACTLY what i'm looking for :P I'm guessing that you wrote it xD So thank-you very much, i really appreciate it :)

~Cody

---

