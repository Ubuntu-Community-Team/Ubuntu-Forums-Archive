---
title: "Mediawiki syntax cleanup."
date: 2011-06-27
forum: Programming Talk
---

### Post by jeffathehutt on 2011-06-27
I'm rather new to mediawiki syntax, and I'm sure there is an easier way to accomplish what I am trying to do.

Basically, I want to include a template on many different pages so that the layout remains consistant, and so maintenance is easier.

I have attached a screenshot showing how the final result should look.  The code below does work fine, but it is very... unreadable. :)

```

{{#if: {{{9|}}} |
    * '''[[{{{1}}}]]'''
    ** {{{2}}}
    *** {{{3}}}
    ** {{{4}}}
    *** {{{5}}}
    ** {{{6}}}
    *** {{{7}}}
    ** {{{8}}}
    *** {{{9}}}
|
    {{#if: {{{7|}}} |
        * '''[[{{{1}}}]]'''
        ** {{{2}}}
        *** {{{3}}}
        ** {{{4}}}
        *** {{{5}}}
        ** {{{6}}}
        *** {{{7}}}
    |
        {{#if: {{{5|}}} |
            * '''[[{{{1}}}]]'''
            ** {{{2}}}
            *** {{{3}}}
            ** {{{4}}}
            *** {{{5}}}
        |
            * '''[[{{{1}}}]]'''
            ** {{{2}}}
            *** {{{3}}}
        }}
    }}
}}

```

(I have added the indentation to make it a bit more readable, on the actual wiki everything is left aligned so that it works properly.  Also, I installed the ParserFunctions extension to get #if)

As it is, I can call this template (Dose) with:

```

{{Dose|one|range1|dose1}}
or...
{{Dose|four|range1|dose1|range2|dose2|range3|dose3|range4|dose4}}

```

The point is, each page will have a different number of ranges, from 1 to 4.  Using the #if statement allows me to display the appropriate number of ranges, depending on how many I pass to the template.

Is there some way to clean up this code, or maybe approach this problem from a different angle?  I'm new to mediawiki but I have a little bit of programming experience (mostly python).

Thanks for any help! :)

---

### Post by simeon87 on 2011-06-27
I have not tried this myself but you could use the [Loop extension to MediaWiki]("http://www.mediawiki.org/wiki/Extension:LoopFunctions") to use a for loop. That way, you can loop from 9 to 1 and check if they exist.

I'm not sure what the MediaWiki code should look like but there's obviously some pattern in there that you could abstract out.

---

### Post by jeffathehutt on 2011-06-27
Wow.  Mediawiki has some very complicated loops! :P

Thanks simeon87 for pointing me to that loop extension.  I ended up actually using the Loops and Variables extensions to accomplish what I wanted.  The code isn't much more readable, however, now it has no upper limit, so instead of just 1-4 items I can now have 1-100.  Also it is a good bit shorter, so that helps with maintenance too. :)

```

{{ #fornumargs: key | value |
{{ #ifeq: {{#var: key}} | 1 | * '''[[{{#var: value}}]]''' |
{{ #ifeq: {{#expr: {{#var: key}} mod 2 }} | 0 |<nowiki/>
** {{#var: value}} |<nowiki/>
*** {{#var: value}}
}}
}}
}}

```

Basically the #fornumargs loop just loops over each numbered argument passed to the template.  So, the template call remains the same, but now the template doesn't have to count how many items were passed, it just loops over each one (up to 100 loops, which is the mediawiki limit).  Thanks again :)

---

