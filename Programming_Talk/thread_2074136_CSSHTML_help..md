---
title: "CSS/HTML help."
date: 2012-10-21
forum: Programming Talk
---

### Post by waloshin on 2012-10-21
I am going crazy with these tables!

What is wrong with this HTML?


```
	<tr> <table class="table_title"> 
		<th>Specs</th>
		<th>Description</th>
		<th>Power</th>
		<th>Operating System</th>
		<th>Price</th>
	 </table> </tr> 
	
	<table class="row">
		<td>Next Gen 1.0 (2012)</td>
		<td>(1)Intel i8 processor 12 core @3.5 GHz, 16 GBs of Ram, 2 TBs of Hard drive</td>
		<td>This is our Next Gen 1.0 Model, you can order the case in black or white</td>
		<td>More powerful then your grandmas computer.</td>
		<td>Waloshin Distro based on Linux 64 bit</td>
		<td>$6000 including tax</td>
	 <tr>
```

This is what it looks like:

[IMG]http://s16.postimage.org/tnk3huo6d/Screen_Shot_2012_10_21_at_12_28_53_AM.png[/IMG]

This is what it needs to look like:

[IMG]http://s10.postimage.org/wynhaw3dl/Screen_Shot_2012_10_21_at_12_30_13_AM.png[/IMG]

The question is where did the lines goes on my table; and why is the title of the table not aligned with the table?

---

### Post by Erik1984 on 2012-10-21
The th and tr elements should be part of the same table, you now have 2 separate tables.

---

### Post by Ji Ruo on 2012-10-21
> **waloshin said:**
> I am going crazy with these tables!

What is wrong with this HTML?

Be glad you aren't using something strict like xhtml! Your problem is the tags aren't nested properly: tr's go inside a table, th's and td's go inside a tr. you need to close one set before starting another.


```
	<table><tr class="table_title"> 
		<th>Specs</th>
		<th>Description</th>
		<th>Power</th>
		<th>Operating System</th>
		<th>Price</th>
	       </tr> 
	       <tr class="row">
		<td>Next Gen 1.0 (2012)</td>
		<td>(1)Intel i8 processor 12 core @3.5 GHz, 16 GBs of Ram, 2 TBs of Hard drive</td>
		<td>This is our Next Gen 1.0 Model, you can order the case in black or white</td>
		<td>More powerful then your grandmas computer.</td>
		<td>Waloshin Distro based on Linux 64 bit</td>
		<td>$6000 including tax</td>
	       </tr>
       </table>
```

Somewhere like stackoverflow.com would be a more appropriate forum for questions like this.

---

### Post by sandyd on 2012-10-21
> **Ji Ruo said:**
> 
Somewhere like stackoverflow.com would be a more appropriate forum for questions like this.

That is why its now in **Programming Talk**
 ;)

---

### Post by kevinharper on 2012-10-22
Remember that most HTML tags come in pairs (open and close).
The second table opens but never closes (table & tr). Here is a basic skeleton for tables:
```

<table>
  <tr>
    <td>DATA</td>
  </tr>
</table>

```
Just add the number of columns you needs by adding more td's, and add to the number of rows by adding more tr's.

---

### Post by lisati on 2012-10-22
[noparse]Another observation: <tr> and </tr> usually go in between <table> and </table>, not the other way round.[/noparse] :D

---

### Post by greenpeace on 2012-10-22
Hey, 

You might want to consider using <thead> and <tbody> tags (possibly <tfoot> as well) to logically separate the table header and body (and footer) content.

This is a good summary, and some example code to get you started: [http://perishablepress.com/html5-table-template/](http://perishablepress.com/html5-table-template/)

hope it helps!

---

### Post by Lars Noodén on 2012-10-22
I strongly recommend either using an editor that does validation for you or running your pages through [tidy](http://tidy.sourceforge.net/) before trying to debug them.  It's in the repositories and easy to add and use. It would catch mistakes like the incorrectly nested tags above.  [Validation](http://validator.w3.org/docs/why.html) is essential for creating a smooth web experience and will also have other advantages like future-proofing your pages.

---

