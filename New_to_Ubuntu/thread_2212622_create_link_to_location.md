---
title: "create link to location"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by Rakesh_vijayan on 2014-03-22
Hi friends

I wish to create document in libreoffice calc .I create a index.ods in directory "hsu" .hsu contain another directory "item" that Item folder contain so many .ods file like 1.ods 2.ods 4.ods .......My wish is that I need to create a link in Index.ods file to corresponding to files in "item's folder " file s .my actual file location of the "hsu" is /home/rakesh/Desktop/hsu/items .....

If I choose the above path if move this folder to another system ,will cause any path problem of the link ? .Please see the pinc it will shows my actual file

---

### Post by Lars Noodén on 2014-03-22
> **Rakesh_vijayan said:**
> 
If I choose the above path if move this folder to another system ,will cause any path problem of the link ? 

It looks like LibreOffice currently only accepts absolute paths for links.  At least that's what I get if I go to :

Insert->Hyperlink->Document->Path

and select a document to link to.  If I modify the path to a relative link, then LibreOffice seems not to eb able to handle it and complains:  *"./file.ods" is not an absolute URL that can be passed to an external application to open it.*  So without relative paths, your remote system will have to have the files in the exact same position in an absolute hierarchy, otherwise they won't work.  :(

It may be that you need to request a new feature upstream.  

How did you make the link?

---

### Post by Rakesh_vijayan on 2014-03-22
> **Lars Noodén said:**
> It looks like LibreOffice currently only accepts absolute paths for links.  At least that's what I get if I go to :

Insert->Hyperlink->Document->Path

It may be that you need to request a new feature upstream.  

How did you make the link?

I hope that you clearly understand my problem Lars Nooden ,I think it was lack of my  knowledge in linux path setting Below pic shows How I make this link  

Thanks again

---

### Post by Lars Noodén on 2014-03-22
There has to be the same hierarchy of directories on both systems (e.g. /home/nadeen/Desktop/soffit/Document/ ) and then the file has to have the same name in both directories.  As I've tried hyperlinking in LibreOffice, it seems not to allow relative paths.  So this would work, if it exists on both systems:

/home/nadeen/Desktop/soffit/Document/file.ods

but this would not

./file.ods

The latter would have been portable and would have worked as long as both files are in the same directory regardless of what that directory is called.  But it seems not to be an option for current  versions of LibreOffice, as far as I can figure it.

I've tried a few different ways but cannot get relative paths to work and get the error message I listed in the previous post.

---

### Post by Rakesh_vijayan on 2014-03-25
Hi every one there is no problem with above scenario. because target folder is with in  base folder 


Thanks

---

