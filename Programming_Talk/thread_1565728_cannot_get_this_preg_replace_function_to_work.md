---
title: "cannot get this preg replace function to work"
date: 2010-09-01
forum: Programming Talk
---

### Post by ELD on 2010-09-01
[php]
class video
{
    public function __construct($text)
    {
    $this->youtube($text, "
[*]");
    }

    public function youtube($text, $code)
    {
        $html = preg_replace("#\[\*\]#", $text, $code);

        return $html;
    }
}  

$video_class = new video("HELLO");

echo $video_class;
[/php]

Can anyone explain what that would error out with:

**Catchable fatal error**:  Object of class video could not be converted to string in **/home/prxainf1/public_html/gamingonlinux.info/test.php** on line **21**

---

### Post by Hellkeepa on 2010-09-01
HELLo!

It means that the object "$video_class" cannot be converted to a string, which is what "echo" expects. Also, your code makes little sense.

Let me explain what it does:
[LIST=1][*]"__contruct ()" is executed upon creating the new object, and recieves the text "HELLO".
[*]This text is then sent to the "youtube ()" method, along with the code "[*]".
[LIST=1][*]The "youtube ()" method replaces the "[*]" pattern in $code with the content of $text ("HELLO")
[*]It then returns the content to the "__construct ()" method.[/LIST]
[*]"__construct ()" does not do anything else, and quits.
[*]"new" returns the newly created object.[/LIST]
As you see, the modified text does not get saved anywhere, which is what I suspect you want to do. Also, since you don't have any "__tostring ()" method, PHP does not know what you want when trying to use the object as an string.

I'd go for a "printVideo ()" method, however.

Happy syncin'!

---

### Post by ELD on 2010-09-01
Of course the code makes no sense, it was an example so i know how to use stuff correctly on code that does something ;)

Besides i figured it out. I know what does what, all i was wandering was what the error meant.

---

