---
title: "about heredoc in php"
date: 2007-07-31
forum: Programming Talk
---

### Post by HansGong on 2007-07-31
<? echo <<<SB<p>I'm "SB".</p>SB; ?>

Parse error: syntax error, unexpected T_SL in /var/www/index.php on line 96

what' wrong with it?

thaks,
Hans

---

### Post by robdor on 2007-08-02
Hey Hans,

The opening and ending sections need to be on their own lines like this:

[PHP]<?
echo <<<SB
    <p>I'm "SB".</p>
SB;
?>[/PHP]


You can read more about it on the php documentation page for strings:
[http://us.php.net/types.string](http://us.php.net/types.string)

Hope that helps,
Rob

---

