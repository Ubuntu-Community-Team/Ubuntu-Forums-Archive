---
title: "[python]HTML parsing and JavaScript"
date: 2008-12-31
forum: Programming Talk
---

### Post by pokerbirch on 2008-12-31
I need to chop up some html and extract a few elements. The actual data i need is within a table which is only a small section of the total html, so i can't see much point in parsing the whole document.

BeautifulSoup seems to be the most used library, however i'm not sure that it will work on this particular html due to JavaScript. You see, some of the links within the table are built using JavaScript, however:
```
soup = BeautifulSoup(html)
```Leaves me with a virtually empty table due to the JavaScript being removed...which renders the 'soup' useless. Is there a way to parse this html by tag names? For instance, let's say i want to extract the table as a parent, and then have each row as a child and each column as a grandchild element...is that possible? The table has a unique 'id' name, so this would seem like a logical key...IF i knew which library/functions to use.

What i want to avoid is using string functions and regex...unless i do them in C...but with so many libs knocking around the 'net, i don't think it will come to that.

---

### Post by pmasiar on 2009-01-01
> **pokerbirch said:**
> I need to chop up some html and extract a few elements.... some of the links within the table are built using JavaScript

You mean some data are added dynamically at the runtime? Then I guess you have quite a big problem to do it right.

---

### Post by pokerbirch on 2009-01-01
> **pmasiar said:**
> You mean some data are added dynamically at the runtime?

Yes. The website in question makes heavy use of JavaScript. This is a (very) simplified version of the table:

[HTML]<table cellspacing="0" id="futureEngagementsTable">
    <tr>
        <td><a href="javascript:profileJumpTo('card','290650')" title="Racecard"
		class="racecard_profile">19:20</a> Fri 2nd Jan </td>
	<td>Wolverhampton</td>
	<td>1m 1f</td>
	<td>5</td>
    </tr>
</table>[/HTML]

As you can probably see/guess, the table is a list of future horse races (we all have bad habits...). From within the JavaScript, i only require the number as that is a unique id which is appended to a base url.

I have done this previously using VB6 under Windows with string functions, however i was hoping to learn more about dom style structures.

---

### Post by pokerbirch on 2009-01-01
Ok, i'll save the DOM stuff for a future project, where i'll be using SOAP and the lxml lib.

Having pulled my head out of the sand...should i:
a) learn regex?
**OR**
b) just port my old VB6 algorithm into either Python or C?

Incidentally, i've been tickling my code with Psyco and Cython. Considering it's only an extra 2 lines at the top of any standard Python script, Psyco seems to be much better (so far..).

---

