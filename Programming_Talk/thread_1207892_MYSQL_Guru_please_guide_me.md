---
title: "MYSQL Guru please guide me"
date: 2009-07-08
forum: Programming Talk
---

### Post by xiaomahe on 2009-07-08
I am using ENCRYPT to encrypt my password, but each time it encrypts the password, it always shows different result, hence i could not compare it when the user login..


any way to solve this ENCRYPT() function in mysql??

I know about MD5 and SHA1, so dun give me this advice, as i just wan to know a way to compare this ENCRYPT password when i want to login..

i am doing this because i am creating mail server, and somehow the tutorial i followed also using ENCRYPT function, in which the saslauthd also use it to authenticate.. I guess, becaue i am not so sure..

in my /etc/pam.d/smtp, i put this value

auth    required   pam_mysql.so user=mail_admin passwd=mahe host=127.0.0.1 db=mysecureemail table=users usercolumn=email passwdcolumn=password crypt=1
account sufficient pam_mysql.so user=mail_admin passwd=mahe host=127.0.0.1 db=mysecureemail table=users usercolumn=email passwdcolumn=password crypt=1

crypt=1 <-- what does this mean? crypt using ENCRYPT?? or can i use md5 as well??

My Courier was made to authenticate with mysql, hence some configuration was done in mysql side.. and this is the file

MYSQL_SERVER localhost
MYSQL_USERNAME mail_admin
MYSQL_PASSWORD mail_admin_password
MYSQL_PORT 0
MYSQL_DATABASE mail
MYSQL_USER_TABLE users
MYSQL_CRYPT_PWFIELD password <--- [COLOR="Red"][SIZE="5"]is this same with ENCRYPT ??[/SIZE][/COLOR]
#MYSQL_CLEAR_PWFIELD password
MYSQL_UID_FIELD 5000
MYSQL_GID_FIELD 5000
MYSQL_LOGIN_FIELD email
MYSQL_HOME_FIELD "/home/vmail"
MYSQL_MAILDIR_FIELD CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/')
#MYSQL_NAME_FIELD



Thanks and i would be very happy if someone can reply me..

---

