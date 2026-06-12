---
title: "Absolute-Relative Form Submit"
date: 2008-12-23
forum: Programming Talk
---

### Post by Nikmaster0 on 2008-12-23
I have this form that I want to submit to a php file, process.php. The form is located in the BETA folder, and the php file is located in the login folder on the same server, so I used this code with this form.
[HTML]<form action="../login/process.php" method="POST">[/HTML]
[HTML]<table align="left" border="0" cellspacing="0" cellpadding="3">
<tr><td>Username:</td><td><input type="text" name="user" maxlength="30" value="<? echo $form->value("user"); ?>"></td><td><? echo $form->error("user"); ?></td></tr>
<tr><td>Password:</td><td><input type="password" name="pass" maxlength="30" value="<? echo $form->value("pass"); ?>"></td><td><? echo $form->error("pass"); ?></td></tr>
<tr><td colspan="2" align="left"><input type="checkbox" name="remember" <? if($form->value("remember") != ""){ echo "checked"; } ?>>
<font size="2">Remember me next time &nbsp;&nbsp;&nbsp;&nbsp;
<input type="hidden" name="sublogin" value="1">
<input type="submit" value="Login"></td></tr>
</table>
</form>[/HTML]
But when I submit the login form, it gives me a 404 error. It worked earlier when I used a relative url and the php file was in the same folder as the fourm in the include subdirectory, but since I want a centralized login server, I need it set up this way. What am I doing wrong?
UPDATE: When I replace ../login/process.php with index.php, it just redirects back to index.php, but that's expected, and I checked the process.php and all it's dependencies, and they are all correct.

---

