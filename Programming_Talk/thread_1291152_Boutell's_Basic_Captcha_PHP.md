---
title: "Boutell's Basic Captcha PHP"
date: 2009-10-14
forum: Programming Talk
---

### Post by Lukas1 on 2009-10-14
Hi I am trying to implement Boutell's basic Captcha referenced here:
[http://www.boutell.com/newfaq/creating/captcha.html](http://www.boutell.com/newfaq/creating/captcha.html)

The installation is supposed to be rather seamless and even has a test script that sends you an email after you pass the Captcha. This is where I am kinda banging my head. I have the script at:
[www.globalcapeesh.com/captcha/demo.php](www.globalcapeesh.com/captcha/demo.php)

and as you can see there is no picture there, however the sound link does work! Now I am really just starting to work with PHP and other than that my programming background is minimal at best. I'd appreciate anyone's help with this. Here's the captcha.php script that it calls out and the package that's online on that link is really small by the way. 

Thank you

<?php
      
        require 'captcha-settings.php';
   
    if (!$login) {
        session_start();
    }
    if (isset($_GET['captchaimg'])) {
        captchaSendImg();
    } elseif (isset($_GET['captchawav'])) {
        captchaSendWav();        
    } else {
        captchaCode();
    }
    function captchaImgUrl()
    {
        global $captchaimg;
        return $captchaimg;
    }
    function captchaWavUrl()
    {
        global $captchawav;
        return $captchawav;
    }
    function captchaCode()
    {
        global $captchaimg, $captchawav;
       
        if (!isset($_SESSION['captchacode'])) {
           
            $chars = "abcdeghijkmnopqrtuvwyz";
            $code = "";
            $length = mt_rand(5, 7);
            for ($i = 0; ($i < $length); $i++) {
                $char = substr($chars, 
                    rand(0, strlen($chars) - 1), 1); 
                $code .= $char;
            }
            $_SESSION['captchacode'] = $code;
        }
        $salt = mt_rand(1000000, 2000000);
        if (isset($_SERVER['SCRIPT_URL'])) {
            $scriptUrl = $_SERVER['SCRIPT_URL'];
        } elseif (isset($_SERVER['SCRIPT_URI'])) {
            $scriptUrl = $_SERVER['SCRIPT_URI'];
        } elseif (isset($_SERVER['REQUEST_URI'])) {
            $scriptUrl = $_SERVER['REQUEST_URI'];
        } else {
            die("captcha.php: SCRIPT_URL, SCRIPT_URI and REQUEST_URI are unavailable, I can't find myself");
        }
        $scriptUrl = preg_replace('/\\?.*$/', '', $scriptUrl);
        $captchaimg = $scriptUrl . "?captchaimg=1&captchasalt=$salt";
        $captchawav = $scriptUrl . "?captchawav=1&captchasalt=$salt";
    }
    function captchaDone()
    {
        if ($_SESSION['captchacode']) {
            unset($_SESSION['captchacode']);
        }
        captchaCode();
    }
    function captchaSendImg()
    {
        global $captchaFont;
        
        if (!isset($_SESSION['captchacode'])) {
            captchaCode();
        }
        $code = $_SESSION['captchacode'];
        $im = imagecreatetruecolor(200, 50);
        imageantialias($im, 1);
        $back = imagecolorallocate($im, 255, 255, 255);
        $fore = imagecolorallocate($im, 0, 0, 0);
        imagefilledrectangle($im, 0, 0, 200, 50, $back);
        $x = mt_rand(10, 20);
        $y = mt_rand(20, 35);
        $length = strlen($code);    
        for ($i = 0; ($i < $length); $i++) {
            $char = substr($code, $i, 1);
            $size = mt_rand(0, 4) + 16.0;
            $angle = mt_rand(0, -45);
            $xoffs = mt_rand(-3, 3);
            $yoffs = mt_rand(-5, 5);
            imagettftext($im, $size, $angle, 
                $x + $xoffs, $y + $yoffs, 
                $fore, $captchaFont, $char);
            $x += 23;
            $code .= $char;
        }
      
        $flakes = (200 * 50) / 16;
        $flakes = mt_rand($flakes * .8, $flakes * 1.2);    
        for ($i = 0; ($i < $flakes); $i++) {
            $x1 = mt_rand(0, 200);
            $y1 = mt_rand(0, 50);
            $x2 = $x1 + mt_rand(-2, 2);
            $y2 = $y1 + mt_rand(-2, 2);
            imageline($im, $x1, $y1, $x2, $y2, $fore);    
        }
       
        header("Content-type: image/jpeg");     
        imagejpeg($im);
        exit(0);
    }
    function captchaSendWav()
    {
        global $captchaSounds;
       
        if (!isset($_SESSION['captchacode'])) {
            captchaCode();
        }
        $wav = "RIFF";
      
        $riffLengthOffset = strlen($wav);
        $wav .= pack("V", 0);
        $wav .= "WAVE";
        # Now the format chunk
        $wav .= "fmt ";
        # Enough room to describe PCM
        $wav .= pack("V", 16);
        # Select PCM
        $wav .= pack("v", 1);    
        # mono
        $wav .= pack("v", 1);
        # samplerate
        $wav .= pack("V", 22050);
        # byterate
        $wav .= pack("V", 22050);
        # block alignment
        $wav .= pack("v", 1);
        # bits per sample
        $wav .= pack("v", 8);
        # Now the data chunk
        $wav .= "data";
        $code = $_SESSION['captchacode'];
        $sound = "";
        $change = mt_rand(7000, 10000);
        $change /= 10000.0;
        for ($i = 0; ($i < strlen($code)); $i++) {
            $char = substr($code, $i, 1);    
            $char = strtolower($char);
            $lsound = file_get_contents("$captchaSounds/$char.ub");
            $llen = strlen($lsound);
            $nsound = "";
            $prev = 0;
            $smoothFrequency = mt_rand(200, 300);
            for ($j = 0; ($j < $llen); $j++) {
                $byte = ord(substr($lsound, $j, 1));
                
                $byte *= $change;
               
                if (mt_rand(0, $smoothFrequency) == 0) {
                    $smooth = ($byte + $prev) / 2.0;
                    $nsound .= pack("C", $smooth);
                }
                $nsound .= pack("C", $byte);
                $prev = $byte;
            }
            $sound .= $nsound;
        }
        $wav .= pack("V", strlen($sound));
        $wav .= $sound;
        
        $wav = substr_replace($wav, pack("V", strlen($wav) - 8),
            $riffLengthOffset, 4);
        $clength = strlen($wav);
        header("Content-length: $clength");
        header("Content-type: audio/wav");     
        echo($wav);
        exit(0);
    }
    function captchaBasePath()
    {
        $src = __FILE__;
        $path = preg_replace('/\/[^\/]+$/', '', $src);
        return $path;
    }
?>

---

### Post by CyberJack on 2009-10-15
When I try to open the image directy (for example: [http://www.globalcapeesh.com/captcha/demo.php?captchaimg=1&captchasalt=1994473](http://www.globalcapeesh.com/captcha/demo.php?captchaimg=1&captchasalt=1994473)) I get the following error:
**Fatal error:** Call to undefined function imageantialias() in **/var/www/captcha/captcha.php** on line **93**

It seems you have the php5-gd package installed which comes with ubuntu.
This package is missing some functions and the only way to correct this is to recompile php with the bundled gd version.
You can find a guide here: [http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)

---

### Post by PartickThistle on 2009-10-15
You could also try this;

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/74647/comments/6](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/74647/comments/6)

---

### Post by Lukas1 on 2009-10-18
Thank you I decided to use recaptcha instead.

---

