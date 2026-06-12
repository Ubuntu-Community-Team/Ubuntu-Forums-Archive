---
title: "Deleting"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by Dirtydeedsman on 2012-10-06
Afternoon chaps

I need help understanding how Ubuntu deletes files and folders from removable media sources. I am using 12.04 LTS and when I delete something from my memory stick (Move to trash) it all disappears and shows up in the trash can but no memory is freed up during the process. When I plug the memory stick into a windows machine i see a .Trash100 folder that contains all the stuff i deleted in my Ubuntu. 

Is there another way of deleting stuff that makes it all go away and free up space without having to format my volume every time?

Thanks

---

### Post by aeronutt on 2012-10-06
> **Dirtydeedsman said:**
> Afternoon chaps

I need help understanding how Ubuntu deletes files and folders from removable media sources. I am using 12.04 LTS and when I delete something from my memory stick (Move to trash) it all disappears and shows up in the trash can but no memory is freed up during the process. When I plug the memory stick into a windows machine i see a .Trash100 folder that contains all the stuff i deleted in my Ubuntu. 

Is there another way of deleting stuff that makes it all go away and free up space without having to format my volume every time?

Thanks
One of:
1) While your media is mounted, after deleting files, empty the trash can.
2) Open a terminal, cd to the media (usual /media/<something>), and type "rm <filename>" or "rm *.*".  Note rm *.* removes all files in the directory your located, use with extreme care. I almost always type "ls *.*" just prior to insure I'm doing what I think I'm doing.
3) There's also a way to add a 'delete' option to the context menu which deletes the files rather than 'move to trash', but I'm not up to speed on how to implement that.

---

### Post by Cheesemill on 2012-10-06
If you hit SHIFT+DEL then the file will be removed completely without moving it to the trash.

---

### Post by aeronutt on 2012-10-06
> **Cheesemill said:**
> If you hit SHIFT+DEL then the file will be removed completely without moving it to the trash.

There we go!! Better than any of my 3 above ;)

---

### Post by Dirtydeedsman on 2012-10-06
Thank you guys, both methods work propeerly.

---

