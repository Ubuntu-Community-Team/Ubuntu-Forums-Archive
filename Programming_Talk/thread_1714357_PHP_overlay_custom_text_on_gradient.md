---
title: "PHP overlay custom text on gradient?"
date: 2011-03-25
forum: Programming Talk
---

### Post by cipherboy_loc on 2011-03-25
I am attempting to create a script (call it image.php) to overlay text on a gradient. The size of the image, the text to be overlapped, the font size, and the colors are all passed as arguments to the script. I have verified that they all arrive, but for some reason, the text never gets put on the image. Would this have anything to with my use of [this]("http://planetozh.com/blog/my-projects/images-php-gd-gradient-fill/") instead of **imagecreatetruecolor()**? Is there any way to get the two to work together?

The code:
[PHP]
<?php
        require_once('/var/www/static/gd-gradient-fill.php');
        $x = $_GET['x'];
        $y = $_GET['y'];

        $text = $_GET['text'];

        $startC = $_GET['start'];
        $startC = "#$startC";

        $endC = $_GET['end'];
        $endC = "#$endC";

        $direction = 'vertical';

        $tColor = $_GET['tc'];
        $tColor = "$tColor";

        $font = $_GET['font'];
        $font = "./SF Old Republic.ttf";

        $size = $_GET['size'];

        $image = new gd_gradient_fill($x, $y, $direction, $startC, $endC);

        $color = imagecolorallocate($image, 0, 0, 0); # Black
        imagettftext($image, $size, 0, 40, $size, $color, $font, $text);

        header('Content-type: image/png');  
        ImagePNG($image);  
        imagedestroy($image);
?>
[/PHP]

Edit:
After looking in "gd-gradient-fill.php" it displayed the image (so I removed it), and instead had it return the this->image variable. Now, it says that the image cannot be displayed because it contains errors. Any ideas on what is happening?

Thanks,
Cipherboy

---

