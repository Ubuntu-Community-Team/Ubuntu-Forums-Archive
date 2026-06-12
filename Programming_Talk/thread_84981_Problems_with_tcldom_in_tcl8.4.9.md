---
title: "Problems with tcldom in tcl8.4.9?"
date: 2005-11-01
forum: Programming Talk
---

### Post by GeirG on 2005-11-01
Hi,

The following small example works well for me in tcl tcl 8.4.7, but
returns nothing in 8.4.9.
Has anybody else seen such a problem?
8.4.7 was used in Hoary, while 8.4.9 is used in Breezy.

First I assign a XML formatted string to a variable:
# set xml "<?xml version=\"1.0\" standalone=\"yes\"
<res s=\"97925911\">
<op id=\"0\" >
<avl>
<ai i=\"1\" v=\"1\" />
</avl>
</op>
</res>"

Then I want to parse it with dom parse:
#::dom::parse $xml

In .7 I get the expected "doc0" response, which I can continue to work
with.
In .9 I only get a blank line, and no errors.

Thanks for any advice.

---

