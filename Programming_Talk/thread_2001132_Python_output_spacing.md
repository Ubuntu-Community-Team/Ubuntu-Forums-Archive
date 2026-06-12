---
title: "Python output spacing"
date: 2012-06-10
forum: Programming Talk
---

### Post by PenguinLuva on 2012-06-10
I'm trying to get certain variables to print out at a certain predefined number of characters into the line. Here are a few pictures to illustrate what I need.

Here's the intended final product:
[IMG]http://i.imgur.com/1LC9J.png[/IMG]

Here's where I need to solve my problem:
[IMG]http://i.imgur.com/pKe2N.png[/IMG]

The item descriptions and prices are going to be of variable length. If I try to use spaces to manually pad my output string, there will be some misalignment obviously. I want to be able to have the prices start a certain number of characters into the output line. Can anybody help me with this?

---

### Post by Vaphell on 2012-06-10
```
>>> len( "product name" )
12
>>> len( "%0.2f" % 10.33 )
5
```

these will tell you how many chars your data occupies and you can do some math with it, eg *print prod_name+(25-len(prod_name))*" "* which would pad string to 25 chars with spaces

crude example
```
prod_w = 25
qty_w = 8
price_w = 10
total_w = 10
sep = "|"

prod = [ "Product 1", "Product 2", "Our Offer of the Day" ]
qty = [ 3, 5, 111 ]
price = [ 0.33, 12.99, 100.11 ]

for i in range(len(prod)):
  prod_c = prod[i] + (prod_w-len(prod[i]))*" "
  qty_c = (qty_w-len("%d"%qty[i]))*" " + "%d"%qty[i]
  price_c = (price_w-len("%0.2f"%price[i]))*" " + "%0.2f"%price[i]
  total_c = (total_w-len("%0.2f"%(price[i]*qty[i])))*" " + "%0.2f"%(price[i]*qty[i])
  print prod_c+sep+qty_c+sep+price_c+sep+total_c

--- output --

Product 1                |       3|      0.33|      0.99
Product 2                |       5|     12.99|     64.95
Our Offer of the Day     |     111|    100.11|  11112.21

```

my advice would be parametrizing the general structure of the document, widths and stuff and using functions that produce proper padding and alignment to fill it, eg
```
def align_left( data, format, width ):
  n = width-len(format%data)
  return format%data + n*" "

def align_right( data, format, width ):
  n = width-len(format%data)
  return n*" " + format%data

def align_center( data, format, width ):
  n = width-len(format%data)
  l = n/2
  r = n/2 + n%2
  return l*" " + format%data + r*" "

# text strings "%s"
print "|"+align_left( "abc", "%s", 10 )+"|"
print "|"+align_right( "abc", "%s", 10 )+"|"
print "|"+align_center( "abc", "%s", 10 )+"|"

# integers "%d"
print "|"+align_left( 1, "%d", 10 )+"|"
print "|"+align_right( 1, "%d", 10 )+"|"
print "|"+align_center( 1, "%d", 10 )+"|"

# floats with 2 decimal places "%0.2f" 
print "|"+align_left( 0.3, "%0.2f", 10 )+"|"
print "|"+align_right( 0.3, "%0.2f", 10 )+"|"
print "|"+align_center( 0.3, "%0.2f", 10 )+"|"
```
output
```
|abc       |
|       abc|
|   abc    |
|1         |
|         1|
|    1     |
|0.30      |
|      0.30|
|   0.30   |
```
if you are aligning by hand, you are doing it wrong ;-) initial amount of work with more structured approach is greater but any reorganization, should the need arise, would be a breeze.

---

### Post by oldfred on 2012-06-10
I found these examples, but have not created invoices. The sample attached was just the code from link below. You do also need to know html, but then can create color, graphics, font sizes etc like any web page, then convert to pdf.

In repository:
python-pisa
[http://freedownload.is/pdf/xhtml-html-css-to-pdf-converter-11590698.html](http://freedownload.is/pdf/xhtml-html-css-to-pdf-converter-11590698.html)
This is the attached test.pdf python code:
[http://nullege.com/codes/show/src%40x%40h%40xhtml2pdf-HEAD%40test%40cookbook.py/43/ho.pisa.CreatePDF/python]("http://nullege.com/codes/show/src%40x%40h%40xhtml2pdf-HEAD%40test%40cookbook.py/43/ho.pisa.CreatePDF/python")
[http://nullege.com/codes/search/ho.pisa.CreatePDF/all/-1/0/python/page:2](http://nullege.com/codes/search/ho.pisa.CreatePDF/all/-1/0/python/page:2)

Some other alternatives:
Simple PDF generation for Python (FPDF PHP port) AKA fpdf.py
[http://code.google.com/p/pyfpdf/downloads/list](http://code.google.com/p/pyfpdf/downloads/list)

HTML/CSS to PDF converter based on Python
[http://pypi.python.org/pypi/xhtml2pdf/](http://pypi.python.org/pypi/xhtml2pdf/)

Creating PDF Invoices discussion/alternatives
[http://stackoverflow.com/questions/270703/creating-pdf-invoices-are-there-any-templating-solutions](http://stackoverflow.com/questions/270703/creating-pdf-invoices-are-there-any-templating-solutions)

email invoice
[http://www.leancrew.com/all-this/2011/11/a-script-to-speed-invoicing-by-email/](http://www.leancrew.com/all-this/2011/11/a-script-to-speed-invoicing-by-email/)
[http://code.activestate.com/recipes/473810-send-an-html-email-with-embedded-image-and-plain-t/](http://code.activestate.com/recipes/473810-send-an-html-email-with-embedded-image-and-plain-t/)

---

### Post by trent.josephsen on 2012-06-10
You can just add a field size to your format specifier to pad each field to a particular length. Given your example I suppose you might want to display your floats as fixed-point (2 decimal places) and pad them to 8 characters, which you can do in two different ways:
```
>>> subtotal=110.60
>>> "{:8.2f}".format(subtotal)      # new, preferred method
'  110.60'
>>> "%8.2f" % (subtotal)            # old printf-like method
'  110.60'
```
Both ways result in a string of size 8.

For your descriptions, you'll want to use the **<** align flag to make the string left-align within the space. Here's what I did to left-align a description within a 20-character field:
```
>>> description="Item 15"
>>> "{:<20}".format(description)
'Item 15             '
```
I don't know how to do that in the printf-like style because when I tried I got a ValueError, but you should use the .format method anyway.

The code to print one of your description+price lines might look something like this:

```
print("{:<20} {:8} {:10.2f}   {:8.2f}".format(description, unit_price, quantity, total))
```

Experiment with it. Python does all the work for you, you just have to know how to ask.

---

