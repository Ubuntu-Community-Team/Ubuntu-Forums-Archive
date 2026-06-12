---
title: "[Vala] How to print all letters from a (UTF) string?"
date: 2010-10-17
forum: Programming Talk
---

### Post by muze4life on 2010-10-17
Hi folks,
Say I have:
string s = "&#22825;&#23433;&#38272;&#24291;&#22580;";
how do I print in a loop each letter at a time till I reach the end of the string?
Notice that it won't work printing each byte at a time since this UTF8 string contains letters larger than one byte.
Any working solutions?

Can't figure out how to do this in Vala..

---

### Post by aanderse on 2010-10-17
i'm not sure how to properly print a single unichar so just ignore the printing part... but this accomplishes what you want:

```

void main () {

string content = "&#22825;&#23433;&#38272;&#24291;&#22580;";

if (!content.validate ()) {

stdout.printf ("invalid utf8 string\n");
return;

}

for (unowned string s = content; s.get_char () != 0; s = s.next_char ()) {

 unichar c = s.get_char ();

 var sb = new StringBuilder ();
 sb.append_unichar (c);
 stdout.printf ("%s\n", sb.str);

}

}


```

you should subscribe and post the the vala mailing list when you have questions

---

### Post by muze4life on 2010-10-17
Thanks a lot! Your code works!
unichar in Vala 0.10 already has a to_string() method, so this is my final version:

[PHP]
void main () {
    string content = "&#22825;&#23433;&#38272;&#24291;&#22580;";

    if (!content.validate ()) {
        stdout.printf ("invalid utf8 string\n");
        return;
    }

    for (unowned string s = content; s.get_char () != 0; s = s.next_char ()) {
        stdout.printf ("%s\n", s.get_char().to_string());
    }
}

[/PHP]

---

