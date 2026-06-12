---
title: "[PHP] Adjusting this thumbnail maker"
date: 2009-09-14
forum: Programming Talk
---

### Post by ELD on 2009-09-14
Basically i followed a tutorial on the web and got myself a php thumbnail maker, only problem is that is ALWAYS makes the thumbnail even if there already is one so i am trying to adjust it so it won't always do it.

This is the code below that sets it all off:
[php]
class thumbnail extends imaging 
{
    private $image;
    private $width;
    private $height;
   
    function __construct($image,$width,$height) 
    {
        parent::set_img("uploads/{$image}");
        parent::set_quality(80);
        parent::set_size($width,$height);
        $this->thumbnail = 'tn_'.pathinfo($image, PATHINFO_FILENAME).'.'.pathinfo($image, PATHINFO_EXTENSION);
        parent::save_img('uploads/thumbnails/' . $this->thumbnail);
        parent::clear_cache();
    }

    function __toString() 
    {
        return $this->thumbnail;
    }
} 
[/php]

I tried adding a file exists action into the constructor and while that would work the "to string" function is always called as far as i know so it throws up errors if we don't run the constructor...i'm not too good with these magic functions so could anyone clear up how i can do this?

---

### Post by Bachstelze on 2009-09-14
We need your whole code to see exactly how things work.

---

### Post by sunchiqua on 2009-09-14
Does this implementation still causes an error ?

[php]class thumbnail extends imaging 
{
    private $image;
    private $width;
    private $height;
   
    function __construct($image,$width,$height) 
    {
        parent::set_img("uploads/{$image}");
        parent::set_quality(80);
        parent::set_size($width,$height);
        $this->thumbnail = 'tn_'.pathinfo($image, PATHINFO_FILENAME).'.'.pathinfo($image, PATHINFO_EXTENSION);
        $thumbnail_path = "uploads/thumbnails/" . $this->thumbnail;
        
        if (!file_exists($thumbnail_path)) {
            parent::save_img($thumbnail_path);
        } else {
            echo "Thumbnail already exists! Exiting ..";
        }
        
        parent::clear_cache();
    }

    function __toString() 
    {
        return $this->thumbnail;
    }
}
[/php]

---

### Post by Linteg on 2009-09-14
Wouldn't it be smarter to check if a thumbnail already exists before doing all the work?
[PHP]
if (file_exists($thumbnail_path))
{
  return
}
else
{
  parent::...
}[/PHP]

---

### Post by ELD on 2009-09-14
> **Linteg said:**
> Wouldn't it be smarter to check if a thumbnail already exists before doing all the work?
[php]
if (file_exists($thumbnail_path))
{
  return
}
else
{
  parent::...
}[/php]

Exactly what i posted in my original post, i already tried it, but the to string function still runs so it can't be a simple file check.

sunchiqua i will look into your code, thanks.

I also don't know why i would have to post the whole code since the only things of value i already show.

Edit > sunchiqua seems like the code works perfectly, thanks a lot!

---

### Post by sunchiqua on 2009-09-14
> **Linteg said:**
> Wouldn't it be smarter to check if a thumbnail already exists before doing all the work?
if (!file_exists($thumbnail_path)) {
            parent::save_img($thumbnail_path);
        } else {
echo "Thumbnail already exists! Exiting ..";
}

That's the only place where you can check if thumbnail exists, without modifying the rest of the code ( generating thumbnail name, etc. ).

---

### Post by Tibuda on 2009-09-14
what about
[php]
    function __construct($image,$width,$height) 
    {
        $this->thumbnail = 'tn_'.pathinfo($image, PATHINFO_FILENAME).'.'.pathinfo($image, PATHINFO_EXTENSION);
        $thumbpath = 'uploads/thumbnails/' . $this->thumbnail;
        if (!file_exists($thumbpath))
        {
            parent::set_img($thumbpath); // I don't know if you need this
        }
        else
        {
            parent::set_img("uploads/{$image}");
            parent::set_quality(80);
            parent::set_size($width,$height);
            parent::save_img($thumbpath);
            parent::clear_cache();
        }
    }
[/php]
?

---

### Post by ELD on 2009-09-14
sunchiqua your code made it work perfectly i checked my ftp and the "last modified" times are now staying still (meaning they are not being generated again!) thanks a lot :D, my pages load a lot faster now too heh!

---

