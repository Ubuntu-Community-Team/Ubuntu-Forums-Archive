---
title: "SQL query help."
date: 2009-04-30
forum: Programming Talk
---

### Post by nateperson on 2009-04-30
I'm pretty new to writting SQL queries.  I've got some of the basics down but...  I'm starting to have some issues... Mostly with Joins... And am hoping someone might be able to give me some help...

Heres what I got, for the tables and columns that I need to get information from.  DBID, Chemical, and CrossReference are the tables.  DBID.OtherWID links to Chemical.WID and CrossReference.OtherWID and CrossReference.CrossWID would link one Chemical.WID to another Chemical.WID.  

I need to display both DBID.XID that have been linked via CrossReference and Chemical.Name that is associated So, here's what I got for my query right now: 

```
SELECT F.DBID.XID, Chemical.Name, S.DBID.XID
FROM DBID S 
INNER JOIN Chemical T
ON S.DBID.OtherWID=T.Chemical.WID
FROM Chemical M
INNER JOIN CrossReference
ON M.Chemical.WID=CrossReference.OtherWID OR M.Chemical.WID=CrossReference.CrossWID
WHERE Chemical.DatasetWID = '19' OR Chemical.DatasetWID = '8';
```

So if someone could help me out with what I'm doing wrong that would be greatly appreciated.

Thanks

Nate

---

### Post by The Cog on 2009-04-30
I can't follow your description of the tables and links. I get the impression that crosslinks joins two chemicals together but you only ask for one chemical name, to I'm not sure I follow your description.

However, here's a wild guess:
SELECT DA.XID, CA.Name, DB.XID, CB.Name
FROM Chemical CA
INNER JOIN DBID DA ON CA.WID = DA.OtherWid
INNER JOIN CrossReference X ON CA.WID = X.OtherWid
INNER JOIN Chemical CB ON CB.WID = X.CrossWID
INNER JOIN DBID DB ON CB.WID = DB.OtherWid
WHERE CA.DatasetWID = '19' OR CA.DatasetWID = '8';

---

### Post by bluelamp999 on 2009-04-30
Hi Nate,

The Cog's wild guess above looks pretty good but your original description is somewhat ambiguous...

If you could post the 3 tables' field layouts (schema) and exactly what you want to achieve in your query it would help...

Good luck

---

### Post by nateperson on 2009-05-01
Sorry, yeah, should've posted the schema when I asked, I been getting a little turned around when trying to follow it... Its all installed and configured on my server with the info from other datasets all loaded.

[http://biowarehouse.ai.sri.com/repos/schema/doc/DBID.html](http://biowarehouse.ai.sri.com/repos/schema/doc/DBID.html)
[http://biowarehouse.ai.sri.com/repos/schema/doc/Chemical.html](http://biowarehouse.ai.sri.com/repos/schema/doc/Chemical.html)
[http://biowarehouse.ai.sri.com/repos/schema/doc/CrossReference.html](http://biowarehouse.ai.sri.com/repos/schema/doc/CrossReference.html)

What I want, I think, is that in the Chemical table there should be many chemicals that are linked to each other via the cross link table.  And essentially I want those that are linked. And I need the name that chemical has in it own dataset, its DBID.XID.  I don't really need the the Chemical.Name, right now, I was really just asking it so I could have it as a reference for the future...

I've tried Cog's wag and gotten an empty set.  I think its cause its unknown if the link in CrossReference.CrossWID or CrossReference.OtherWID.  Thats why I tried to throw an OR in there.  and Cog's seems to assume its one place or the other...

Thanks for your help so far!

---

### Post by nateperson on 2009-05-01
I'm now pretty sure I understand what Cog suggested, and I'm also pretty sure its correct and should give me what I need...  

What I'm not sure about is why its returning a null set even after I take out the WHERE statement in the query, cause in the 30,000k+ rows in the CrossReference table, there should be at least 1... but I think that's my problem....  and I need to go back and look at the loaders... cause I know the stuff is/should be there....

Thanks again,

Nate

---

