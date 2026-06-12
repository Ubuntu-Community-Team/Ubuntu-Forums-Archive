---
title: "How to split Glib::ustring?"
date: 2010-03-01
forum: Programming Talk
---

### Post by kahumba on 2010-03-01
Folks, I can't find a split function in Glib::ustring.
What's the right way to do this? Can anyone please post a snippet?


ps: in case it matters, I need to split the Glib::ustring by the new line character "\n".

---

### Post by PaulM1985 on 2010-03-01
I haven't testing this code, but I think you should be able to do something like:

```

// String to split
ustring aString("Some text \n the rest");

// Position of the new line in the string
int newLine = aString.find_first_of('\n');

// The first part up to the new line
ustring start = aString.substr(0, newLine);

// The part after the new line
ustring end = aString.substr(newLine, aString.length() - newLine);

```

If you have multiple lines, repeat the process on the created "end" variable until find_first_of() can't find a new line.

Like I said, I haven't tested it but this should be a decent starter.

Paul

ustring docs: [http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1ustring.html](http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1ustring.html)

---

### Post by kahumba on 2010-03-01
Thanks, that's what I was about to do anyway, I just hoped there's a simple way to do this since it's such a common task, in Java it's as simple as:
String[] myLines = allLines.split("\n");
And I'm done.
I **hope** there's some utility in glib that works with Glib::ustring.. otherwise it's a bit disappointing..

---

### Post by kahumba on 2010-03-01
Oh there we go, I just found a short working solution..

[PHP]
void test() {
    Glib::ustring str = "Line 1\nLine 2\nLine 3\nLine 4";
    std::vector<Glib::ustring> vLines = Glib::Regex::split_simple("\n", str); //THIS IS IT!!
    std::cout << "size: " << vLines.size() << std::endl;
    for(int i=0; i<vLines.size(); i++) {
        std::cout << vLines.at(i) << std::endl;
    }
}
[/PHP]

---

### Post by PaulM1985 on 2010-03-01
After looking at the docs it doesn't seem like there is one.  If this is something that you want to do alot throughout your program it may be worth making your own string class which extends ustring with the added functionality.  (Maybe returning a std::vector<String>).

Paul

You beat me.  No need to create your own class then.

---

### Post by kahumba on 2010-03-01
:)

---

