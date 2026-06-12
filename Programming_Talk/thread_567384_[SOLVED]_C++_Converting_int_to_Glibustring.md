---
title: "[SOLVED] C++: Converting int to Glib::ustring"
date: 2007-10-04
forum: Programming Talk
---

### Post by aaaantoine on 2007-10-04
If I try to append or += an int to a Glib::ustring, I get a compiler error.  My attempts to cast the int as a char* or a ustring lead to segmentation faults.

Is there a built-in function to convert int to ustring, or will I have to program my own function for this?

Thanks.

---

### Post by MicahCarrick on 2007-10-04
Perhaps this will help: [http://library.gnome.org/devel/glib/unstable/glib-String-Utility-Functions.html#g-ascii-dtostr]("http://library.gnome.org/devel/glib/unstable/glib-String-Utility-Functions.html#g-ascii-dtostr")

---

### Post by ryno519 on 2007-10-04
The types are incompatible. Glib::ustring has no copy or append operators for any types but Glib::ustring and std::string (as far as I know). This really only leaves you with one option. You will need to use a std::ostringstream to convert your integer into an std::string, which can be appended to your Glib::ustring. Consider the following function.

```

Glib::ustring IntToUString(int iVal)
{
    std::ostringstream ssIn;
    ssIn << iVal;
    Glib::ustring strOut = ssIn.str();

    return strOut;
}

```

This code will take an integer as an input and output that integer as a Glib::ustring. You could get creative with this and add a template to that function which would allow you to convert any supported type to a Glib::ustring, not just ints.

Edit: Glib::ustring probably also has a copy and append operator for a char*.

---

### Post by aaaantoine on 2007-10-04
Thanks for the tip.  I never quite found my way around all the C++ objects.  There's a lot of them...

I had to do a bit of extra digging to find that std::ostringstream requires #include <sstream>.  Just FYI to curious readers.

---

### Post by ryno519 on 2007-10-04
> **aaaantoine said:**
> Thanks for the tip.  I never quite found my way around all the C++ objects.  There's a lot of them...

I had to do a bit of extra digging to find that std::ostringstream requires #include <sstream>.  Just FYI to curious readers.

I have a tutorial/reference book, "The C++ Standard Library" by Nicolai Josuttis. It comes in quite handy.

---

