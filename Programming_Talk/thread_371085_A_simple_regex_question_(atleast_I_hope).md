---
title: "A simple regex question (atleast I hope)"
date: 2007-02-26
forum: Programming Talk
---

### Post by b4t3m4n on 2007-02-26
I have a block of text, one continuous string.  The original document was on multiple lines, and the line breaks are translated in the string as \n's.

Within the text, field labels are like this

Employer: John Doe
Status: Boss

I have no problem pulling out all the Employers with a ```
 /Employer:\s+(.+)/
```


But one part of the record is a list of  items that are displayed like so

List of Items:

Item one
Item two
Item three

The problem being ```
/List of items:( .+ )/
```doesn't work because .+ still stops on \n so that expression returns nothing.  If I do ```
/List of items:( .+ )/m
```  it works but also returns all the \n's.  So basically I want to pull in each item in the list but ignore the \n's.

If you want more information, let me know.  I am using the string.scan(regex) function in ruby, which returns every match in an array of strings.

---

### Post by kidders on 2007-02-27
Hi there,

I'm not very familiar with Ruby ... I tried this in PHP (which I presume makes no difference), but I ran into two problems:

[LIST]
[*]It's easy to write a regex that won't capture the **\n**'s, but only by using nested subpatterns ... which means the regex parser will probably only remember the last list item. That's clearly useless. :-(
[*]The only way I could find of knowing when to stop matching list items was to assume no list item could end with ':' ... which probably isn't a valid assumption. :-(
[/LIST]

I had more success with files formatted this way ...
```
Employer: Jon Doe
Status: Boss
List of items: Item one
List of items: Item two
List of items: Item three
```
... because I could programatically attach a meaning to the fact that some values had the same label (ie the name of the list), and didn't run into the following problem:

```
Employer: Jon Doe
Status: Boss
List of items:
Item one
Item two**:**
Item three
```

Is that any help?

**Edit:** Is your text block small enough (or infrequently parsed enough) to make some initial transformations feasible?

---

### Post by Enselic on 2007-02-27
> **b4t3m4n said:**
> 
If you want more information, let me know.  I am using the string.scan(regex) function in ruby, which returns every match in an array of strings.

If you use ruby you could simply enter a loop when you encounter a list, and collect non-whitespaced lines as items until there is a line with a :.

Something like

```

if /List of items:/ =~ row
  row = file.next_row
  list_items = []
  while ! /:/ =~ row
    list_items << row unless /\s*/ =~ row
    row = file.next_row
  end

  # Now `list_items' contains the items.
elsif /Employer:\s+(.+)/ =~ row
  # etc...
end

```

---

