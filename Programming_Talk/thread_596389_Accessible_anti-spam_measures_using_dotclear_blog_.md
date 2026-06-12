---
title: "Accessible anti-spam measures using dotclear blog software"
date: 2007-10-29
forum: Programming Talk
---

### Post by matthew on 2007-10-29
[I have a blog]("http://matthewhelmke.net") that I set up using [dotclear]("http://www.dotclear.net/"). I am very impressed by the PHP and xhtml in the package, but almost all of the comments and support is in French. I can read a bit, but this has been a little bit of a struggle for me at time.

The blog works great and I love dotclear as a package as it is clear, well written, with good error checking and is fully xhtml compliant. But, this week I've had a lot of comment spam. I wanted to do something as an anti-spam measure that allowed the site to remain accessible to text browsers, the blind, and so on. 

All I have found so far that is specifically for dotclear [is this]("http://www.dotclear.net/trac/wiki/DotClear/Plugins#Captcha"), and it isn't as accessible as I would prefer, so I am very hesitant to use it...plus, all the documentation is in French, and that makes it difficult for me.

I have been looking at [reCAPTCHA]("http://recaptcha.net/"), and I really like the idea and everything noted on the site, but I am having some trouble installing it. I can get it to show up on my comment pages, but it seems to be completely ignored.

My gut feeling is that I am not following the logic flow of dotclear correctly, and that somehow the captcha check isn't being performed at all. I'll post some of the relevant bits from my blog software momentarily, but for those who don't want to read them, or don't know PHP, I am also interested in any other ideas you may have for spam prevention, so please feel free to comment.

Okay, here are the relevant bits of code...first, the comment submit form.
```
<form action="<?php dcPostUrl(); ?>" method="post" id="comment-form">

<script>
var RecaptchaOptions = {
   theme : 'clean'
};
</script>

<fieldset>
    <?php dcCommentFormError('<div class="error"><strong>Erreurs :</strong><br /> %s</div>'); ?>
    <?php dcCommentFormMsg('<p class="msg"><strong>%s</strong></p>'); ?>
    <p class="field"><label for="c_nom">Name :</label>
    <input name="c_nom" id="c_nom" type="text" size="30" maxlength="255"
    value="<?php dcCommentFormValue('c_nom'); ?>" />
    </p>

    <p class="field"><label for="c_mail">Email (optional) :</label>
    <input name="c_mail" id="c_mail" type="text" size="30" maxlength="255"
    value="<?php dcCommentFormValue('c_mail'); ?>" />
    </p>

    <p class="field"><label for="c_site">Site Web (optional) :</label>
    <input name="c_site" id="c_site" type="text" size="30" maxlength="255"
    value="<?php dcCommentFormValue('c_site'); ?>" />
    </p>
    
    <p class="field"><label for="c_content">Comment :</label>
    <textarea name="c_content" id="c_content" cols="35" rows="7"><?php
    dcCommentFormValue('c_content');
    ?></textarea>
    </p>

    <p class="form-help">
    Thank you for your comments!
    </p>

    <p><input type="checkbox" id="c_remember" name="c_remember" />
    <label for="c_remember">Remember my information</label>
    </p>

<?php
  # This is the code for reCAPTCHA, to prevent spam and help digitize books. See http://recaptcha.net

  require_once('/home/******/recaptchalib.php');
  # Get a key from http://recaptcha.net/api/getkey

  $publickey = "******";
  $privatekey = "******";

  # will be the response from reCAPTCHA
  $resp = null;
  # will be the error code from reCAPTCHA, if any
  $error = null;

  # are we submitting the page?
  if ($_POST["submit"]) {
    $resp = recaptcha_check_answer ($privatekey,
                                    $_SERVER["REMOTE_ADDR"],
                                    $_POST["recaptcha_challenge_field"],
                                    $_POST["recaptcha_response_field"]);

  if ($resp->is_valid) {
    echo 'Thank you!';
    # in a real application, you should send an email, create an account, etc
    } else {
    die ("The reCAPTCHA wasn't entered correctly. Please try again." .
    "(reCAPTCHA said: " . $resp->error . ")");
    $error = $resp->error;
    }
  }
  echo recaptcha_get_html($publickey, $error);
?>

    <p><input type="submit" class="preview" name="preview" value="preview" />
    <input type="submit" class="submit" value="submit" />
    <input type="hidden" name="redir" value="<?php dcCommentFormRedir(); ?>" /></p>
</fieldset>

</form>
```With this code sample (the captcha bit I know really doesn't do anything by way of meaningful output...I'm just trying to get it implemented first, then I'll add the actual actions), the captcha appears on the site perfectly (don't look right now, I don't have it live...it is only on my testbox). However, when clicking to submit, it doesn't matter whether anything is in the captcha box or not, the submission goes through as if it wasn't there.

I followed the submission trail to find where the input validation occurs, but I can't seem to figure out how or what to change to make any difference...I'm hoping this is just something simple and silly that I'm missing and that another set of eyes can help me see what is probably glaringly obvious. The recaptchalib.php is correctly installed and accessible to the quoted script.

I guess I'm hoping for one of several possiblities...either that there is someone here familiar with dotclear who can help me figure out the logic flow of the blog software so I can correctly install this captcha, or that there is someone here who can find a silly error or omission that I am making...or that there is someone here with an even better anti-spam idea.

---

