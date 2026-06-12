---
title: "Drop common lines at head/tail of a large set of files"
date: 2009-05-17
forum: Programming Talk
---

### Post by dobry_den on 2009-05-17
Hi! I have a large set of pairs of text files (each pair in their own subdirectory) and each pair shares head/tail (a couple of first and last lines) but differs in the middle part. I need to delete the heads/tails and keep only the middle portions in which they differ. The lengths of heads/tails are not the same (in terms of number of lines) for different pairs. Do you know an easy way to delete all the heads (tails) at once for all the files? Thanks a lot in advance!

---

### Post by ghostdog74 on 2009-05-17
show examples of those files, and show the desired output

---

### Post by dobry_den on 2009-05-17
for example:

file1
> 
A Window on Russia

Mind and Matter

Health and Medicine

Science and Society

Home / Commentaries / Rasov&#283; rozd&#283;lená Evropa

Article available in:

Rasov&#283; rozd&#283;lená Evropa

by Alberto Alesina and Francesco Giavazzi

Alberto Alesina

Francesco Giavazzi

Typickým znakem evropské extrémní pravice je její rasismus a to, že využívá imigra&#269;ní otázku ve sv&#367;j politický prosp&#283;ch. Italská Lega Nord, nizozemský Vlaams blok, francouzská Le Penova Front national - to vše jsou p&#345;íklady stran &#269;i hnutí vzešlých ze spole&#269;né averze v&#367;&#269;i imigrant&#367;m a prosazujících zjednodušující pohled na to, jak &#345;ešit otázku p&#345;ist&#283;hovalc&#367;. Zatímco individua jako Jörg Haider &#269;i Jean-Marie Le Pen p&#345;icházejí a (nikdy ne dost brzy) odcházejí, otázka rasy a rasismu z evropské politiky jen tak hned nevymizí.

Copyright: Project Syndicate, kv&#283;ten 2002

P&#345;etisk materiálu z t&#283;chto webových stránek bez písemného souhlasu Project Syndicate je porušením mezinárodního autorského práva. Chcete-li si svolení zajistit, kontaktujte prosím [email]distribution@project-syndicate.org[/email] .

You must be logged in to post a comment. Please log in or sign up for a free account.

Home Contact Us

About Us Contributors Commentaries Member Papers Support Us Editors' Forum Site Map



file2
> 
A Window on Russia

Mind and Matter

Health and Medicine

Science and Society

Home / Commentaries / La maison raciale divisée de l'Europe

Article available in:

La maison raciale divisée de l'Europe

by Alberto Alesina and Francesco Giavazzi

Alberto Alesina

Francesco Giavazzi

L'extrême droite européenne est caractérisée par son racisme et son utilisation de la question de l'immigration en tant que divergence politique. La Lega Nord en Italie, les Vlaams Blok aux Pays-Bas, les partisans du Front national de Le Pen en France, constituent tous des exemples de partis ou de mouvements formés sur le thème courant de l'aversion envers les immigrants et la promotion de politiques simplistes pour les contrôler. Alors que des individus comme Jorg Haidar et Jean-Marie Le Pen peuvent aller et (jamais assez tôt) venir, la question raciale ne disparaîtra jamais de la politique européenne dans un futur proche.

Copyright : Project Syndicate, mai 2002

Toute reproduction du contenu de ce site sans accord écrit de Project Syndicate constitue une infraction à la législation internationale relative au droit d’auteur. Pour obtenir une autorisation, merci de nous contacter à l’adresse suivante : [email]distribution@project-syndicate.org[/email] .

You must be logged in to post a comment. Please log in or sign up for a free account.

Home Contact Us

About Us Contributors Commentaries Member Papers Support Us Editors' Forum Site Map


result file1:
> 
Home / Commentaries / Rasov&#283; rozd&#283;lená Evropa

Rasov&#283; rozd&#283;lená Evropa

Typickým znakem evropské extrémní pravice je její rasismus a to, že využívá imigra&#269;ní otázku ve sv&#367;j politický prosp&#283;ch. Italská Lega Nord, nizozemský Vlaams blok, francouzská Le Penova Front national - to vše jsou p&#345;íklady stran &#269;i hnutí vzešlých ze spole&#269;né averze v&#367;&#269;i imigrant&#367;m a prosazujících zjednodušující pohled na to, jak &#345;ešit otázku p&#345;ist&#283;hovalc&#367;. Zatímco individua jako Jörg Haider &#269;i Jean-Marie Le Pen p&#345;icházejí a (nikdy ne dost brzy) odcházejí, otázka rasy a rasismu z evropské politiky jen tak hned nevymizí.

Copyright: Project Syndicate, kv&#283;ten 2002

P&#345;etisk materiálu z t&#283;chto webových stránek bez písemného souhlasu Project Syndicate je porušením mezinárodního autorského práva. Chcete-li si svolení zajistit, kontaktujte prosím [email]distribution@project-syndicate.org[/email] .


result file2
> 

Home / Commentaries / La maison raciale divisée de l'Europe

La maison raciale divisée de l'Europe

L'extrême droite européenne est caractérisée par son racisme et son utilisation de la question de l'immigration en tant que divergence politique. La Lega Nord en Italie, les Vlaams Blok aux Pays-Bas, les partisans du Front national de Le Pen en France, constituent tous des exemples de partis ou de mouvements formés sur le thème courant de l'aversion envers les immigrants et la promotion de politiques simplistes pour les contrôler. Alors que des individus comme Jorg Haidar et Jean-Marie Le Pen peuvent aller et (jamais assez tôt) venir, la question raciale ne disparaîtra jamais de la politique européenne dans un futur proche.

Copyright : Project Syndicate, mai 2002

Toute reproduction du contenu de ce site sans accord écrit de Project Syndicate constitue une infraction à la législation internationale relative au droit d’auteur. Pour obtenir une autorisation, merci de nous contacter à l’adresse suivante : [email]distribution@project-syndicate.org[/email] .


only the lines at which the files differ were kept

---

### Post by sujoy on 2009-05-17
i got an idea :D
diff the two files and store in a third one
diff file1 file2 > file3

now for lines in file3 that start with '<' store the rest of the line in file1 and for lines in file3 that start with '>' store the rest of the lines in file2
ignoring '<' and '>' respectively.

---

### Post by kaibob on 2009-05-17
I suspect ghostdog74 has an awk 1-liner that will do it all, but building on sujoy's suggestion:

```
diff file1 file2 | awk '/>/ { print substr($0, index($0,$2)) "\n" }' > newfile2
``` 

and

```
diff file1 file2 | awk '/</ { print substr($0, index($0,$2)) "\n" }' > newfile1
```

---

### Post by jon zendatta on 2009-05-17
[PHP]cat file2[/PHP]

[PHP]sort file1 > file2[/PHP]


[PHP]uniq file2[/PHP]
or...

[PHP]sort file | uniq[/PHP]

---

### Post by ghostdog74 on 2009-05-17
```

awk 'FNR==NR{_[++d]=$0;next}$0!~_[FNR]{print $0"->"_[FNR]}' file1 file2

```

---

