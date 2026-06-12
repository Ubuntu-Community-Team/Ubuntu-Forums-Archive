---
title: "Website Debugging"
date: 2013-10-08
forum: Programming Talk
---

### Post by TheodoreP on 2013-10-08
Hello,
Seems like ages since I was last on here, but I really need some help. I have website hosted at sociablecooking dot com and for some time now my recipe for old-fashioned kettle corn has been out of line. By that I mean it is indented just enough to be a noticeable problem. I have no idea what is wrong with my code seeing as to how it is a php file that creates the list of recipes. Any input on how to solve this would be greatly appreciated. As well if you have ideas for additional features and perhaps you have an idea for a new look. I will welcome all ideas, not necessarily will I take all suggestions to heart but your idea is likely to stick in my head for sometime and some version of it will probably be implemented?
 
I thank you for all your help and please feel free to register with my site. One lifetime goal I have is to overshadow all other recipe sharing site and if I can get a hold of sociable I will be shooting for overshadowing all social networks (which would take a lot of effort)!

MasterProgram

---

### Post by Erik1984 on 2013-10-08
Firefox has great tools for analyzing your site. Right-click somewhere and pick "inspect element", this toggles the developer tools. You can browse through all elements on the page and look at their properties. This shows me that the TD element surrounding the image on the second row is bigger than the TDs on the other three rows. That pushes the text and button further to the right. Don't know why that TD is bigger but just to give you a starting point.

---

### Post by spjackson on 2013-10-08
Each of the recipes has it's own independent table, and each of these just happen to layout columns that line up vertically. The kettle corn one is different because the description does not overflow to a second line. A work-around is to write a bit more for that description. I can't really suggest a good way to align the columns that would work with the existing data. Perhaps setting some fixed column widths might do the trick.

---

### Post by TheodoreP on 2013-10-08
Yes, I saw that too, Euroman! But if you look at the code for those td elements there all the same.

I thank you Jackson for your advice I'll try it.

---

