---
title: "html table border"
date: 2007-01-26
forum: Programming Talk
---

### Post by glederfein on 2007-01-26
Hi all!
I have an HTML question.
Let's say I have an HTML table with 3 columns and I want there to be an external border around the first two columns only. How do I go about doing that?

---

### Post by JamieC on 2007-01-26
Assign a class to the first two columns only?

---

### Post by glederfein on 2007-01-26
> **JamieC said:**
> Assign a class to the first two columns only?
By "class" do you mean CSS class? How do I apply that? Can you please give an example?

---

### Post by JamieC on 2007-01-26
Sure, here you go:
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <style type="text/css">
    /*<![CDATA[*/
      .bordered
      {
          border: 1px solid #000000;
      }
    /*]]>*/
    </style>
    <title></title>
  </head>
  <body>
    <table>
      <tr>
        <td class="bordered">foo</td>
        <td class="bordered">bar</td>
        <td>foo</td>
      </tr>
    </table>
  </body>
</html>

```

---

### Post by glederfein on 2007-01-26
I understand I can play around with the borders around each specific cell but I'm talking about the table border (<table border='1'>). Can I make **this** border rap around the first two columns only?

---

### Post by phossal on 2007-01-26
The table is a box. All of the columns are *in* the box. So you can't put a table border around only two of the things in the box if there are three.

What you have to do is add individual borders to the cells to make it *appear* one continuous border envelopes the area you've chosen. For example, add top borders to both columns. Add a left border to the left column, a right border to the right column, and then bottom borders to both. The third column will have no borders.

---

### Post by JamieC on 2007-01-26
Are you using tables for a table based layout or for presenting tabular data?

---

### Post by yaaarrrgg on 2007-01-26
Another possible solution is to think of the border as a 1 pixel wide (or tall) cell.  So, you might not  create a 3x3 table, but 5x5 table, for example.  Then drop in a single pixel gif as a background of the thin cells and size them to 1 pixel wide or tall.  That is, if you are not comfortable using CSS...

---

### Post by yaaarrrgg on 2007-01-26
> **glederfein said:**
> I understand I can play around with the borders around each specific cell but I'm talking about the table border (<table border='1'>). Can I make **this** border rap around the first two columns only?

Not really...  unless you nest tables, which might not be what you want.  It might not be easy to keep the rows aligned if you do this.  For example, you might have a two column table in the cell of another two column table (totally 3 columns).

---

### Post by JamieC on 2007-01-26
Here's the solution which phossal detailed of:
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <style type="text/css">
    /*<![CDATA[*/
      td
      {
          float: left; // Bring columns together
      }
      .left_bordered, .right_bordered
      {
          border-top: 1px solid #000000;
          border-bottom: 1px solid #000000;          
      }
      .left_bordered
      {
          border-left: 1px solid #000000;
      }
      .right_bordered
      {
          border-right: 1px solid #000000;
      }
    /*]]>*/
    </style>
    <title></title>
  </head>
  <body>
    <table>
      <tr>
        <td class="left_bordered">foo</td>
        <td class="right_bordered">bar</td>
        <td>foo</td>
      </tr>
    </table>
  </body>
</html>

```

---

### Post by glederfein on 2007-01-26
> **phossal said:**
> The table is a box. All of the columns are *in* the box. So you can't put a table border around only two of the things in the box if there are three.

What you have to do is add individual borders to the cells to make it *appear* one continuous border envelopes the area you've chosen. For example, add top borders to both columns. Add a left border to the left column, a right border to the right column, and then bottom borders to both. The third column will have no borders.
Can you please show an example of how to do this? I'm getting quite confused... :(

---

### Post by JamieC on 2007-01-26
> **glederfein said:**
> Can you please show an example of how to do this? I'm getting quite confused... :(

See my previous post.

---

### Post by phossal on 2007-01-26
```
<style>
	.left {border-left: 1px solid black;}
	.right{border-right: 1px solid black;}
	.top {border-top: 1px solid black;}
	.bottom {border-bottom: 1px solid black;}
</style>

<table cellpadding=0 cellspacing=0 >
	<tr>
		<td class='left top bottom'>Column 1<td>
		<td class='right top bottom'>Column 2<td>
		<td>Column 3<td>
	</tr>
</table>
```

---

