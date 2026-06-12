---
title: "inserting sequential divs"
date: 2012-08-30
forum: Programming Talk
---

### Post by maclenin on 2012-08-30
I am trying to solve the following.

I have a box...
```
#box {width:100px; height:50px;}
```
...into which I'd like to insert/append...
```
#frame0,
#frame1,
#frame2 {float:left; margin:5px auto 0 5px; width:30px; height:30px;}

```
...which would then be ready to accept...
```
var photo=new Array();
photo[0]="image0.jpg";
photo[1]="image1.jpg";
photo[2]="image2.jpg";
var lenP=photo.length;
```
...using the following method:
```
function insert_images()
{
for (i=0; i<lenP; i++)
{
document.getElementById("box").innerHTML='<div id="frame'+i+'">'+photo[i]+'</div>';
}
}
```
The result I see is, roughly:
```
<div><box><div><frame2><image2></div></div>
```
The result I am shooting for is:
```
<div><box>
<div><frame0><image0></div>
<div><frame1><image1></div>
<div><frame2><image2></div>
</div>
```
Perhaps this analogy helps clarify what I am after.
```
cat photo0 photo1 photo2 >> box_frame
```
...when one opens box_frame one finds...
```
image0 image1 image2
```
...and not just:
```
image2
```

Thanks for any insight.

---

### Post by ofnuts on 2012-08-30
Your code replaces the innerHTML instead of appending to it...

---

### Post by maclenin on 2012-08-30
**ofnuts!**

You are spot on. Therein lies the problem. I would rather append than replace. 

Is there a way to tweak my code to make it append rather than replace?

Thanks for the wisdom.

---

### Post by Vaphell on 2012-08-30
```
document.getElementById("box").innerHTML **+=** '<div>...</div>'
```

---

### Post by maclenin on 2012-08-30
**Vaphell!**

Dzi&#281;kujemy!

[Can you divulge a source for such knowledge? Or is that nugget something you simply chalk up to experience? Thank you, again!]

---

### Post by ofnuts on 2012-08-31
> **maclenin said:**
> **Vaphell!**

Dzi&#281;kujemy!

[Can you divulge a source for such knowledge? Or is that nugget something you simply chalk up to experience? Thank you, again!]
With all due to respect t Vaphell, this was fairly obvious... JS would be a very poor language if it didn't allow it.

---

### Post by maclenin on 2012-08-31
**ofnuts!**

Being a "home schooled" coder, I've come to rely on this forum and google - in that order, really - to help me understand the dirty bits....

**Vaphell** was playing his part in sustaining a tradition of taking time to offer a questioner relevant and responsive guidance no matter how obvious or arcane that advice might need to be!

Dzi&#281;kujemy, again!

---

