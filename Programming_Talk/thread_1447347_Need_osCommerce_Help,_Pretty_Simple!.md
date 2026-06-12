---
title: "Need osCommerce Help, Pretty Simple!"
date: 2010-04-05
forum: Programming Talk
---

### Post by ECommercer on 2010-04-05
Hello guys, my name is Justin, and I need some help with my [site]("http://www.eastcoastairsoft.com").  As you can see on the left hand side, there are main categories that each have subcategories listed out below them. For certain categories, I would like to permanently hide the subcategories.  Somebody had suggested Javascript, but then I think that search engine spiders can still see those subcategory links.  If anybody could help me selectively hide subcategories for some main categories, but not others, that would be GREAT, and I would be so happy.  Thanks!!

---

### Post by cdekter on 2010-04-05
Don't you think it would be better to post this kind of question on osCommerce forums?

At a high level, the best way would probably be to add a boolean field to the categories table, indicating whether to display the subcategories for a given record. Then change the home page code to test this field and not output the subcategory links if the value is false (or whatever).

---

### Post by Bucky Ball on 2010-04-05
[http://forums.oscommerce.com/](http://forums.oscommerce.com/)

That easy. Are you looking for hits on your site?

---

