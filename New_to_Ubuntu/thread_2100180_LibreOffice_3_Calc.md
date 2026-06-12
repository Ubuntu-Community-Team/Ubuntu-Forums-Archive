---
title: "LibreOffice 3 Calc"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by wstay on 2012-12-31
I am using LibreOffice 3 Calc.
Please refer to Screenshot-1.
When I post 1/1 into cell A1 it gives me 01/01/13.
When I post 31/1 into cell B1 it gives me 31/1.
What I need is when I post 1/1 into cell A1 I should get 1/1.
I tried Cell Formatting for A1 to get 1/1 instead of 01/01/13
by following the Cell Format for Cell B1 as in Screenshot-2 and I get the number 41275 instead of 1/1 in Cell A1 as in screenshot-3.
Can someone please help.

---

### Post by vasa1 on 2012-12-31
No matter what you do, you should normally not see 1/1 as the result of typing 1/1 into a cell and hitting enter. It should show as 1 or 1.0 or 1.00 etc or as a date (formatted as per your locale) or as a multi-digit number that can be converted to a date with the appropriate formatting.

If you really want to see 1/1 in a cell after typing 1/1, that cell has to be formatted as text. Alternatively you could type '1/1 instead of just 1/1 where the ' is a single quote and not the grave key (the thing below the ~ aka tilde).

---

