---
title: "[SOLVED] PHP + MySQL, Call to undef function"
date: 2008-05-26
forum: Programming Talk
---

### Post by ladjack on 2008-05-26
Hello, everybody =)

here is my problem:

```
Fatal error: Call to undefined function  mysql_fetch_array() in /home/ladjack/public_html/News/news.php on line 20
```

here is line #20:

```
while($Years = mysql_fetch_array($resS))
```

what could it be? I have php5-mysql installed, extensions such as 'mysql.so' and 'mysqli.so' are enabled and corresponding files exists.

thnx in advance =)

---

### Post by LaRoza on 2008-05-26
Do the other MySQL functions work? If you installed these modules after starting Apache/PHP, you'll have to restart it.

---

### Post by ladjack on 2008-05-26
> **LaRoza said:**
> Do the other MySQL functions work?

For example: mysql_num_row() works great, 'mysql_connect' and 'mysql_select_db' also.

LAMP installation instructions from [here]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP")

---

### Post by Verminox on 2008-05-26
What about mysql_fetch_assoc? Can you post the rest of the code?

---

### Post by ladjack on 2008-05-26
> **Verminox said:**
> What about mysql_fetch_assoc? Can you post the rest of the code?

```

...skip
connecting to mysql server...
selecting db...
...skip

$sqlS = "SELECT Year_Name FROM Years";
$resS = mysql_query($sqlS);

	if(!$resS)
	{
		echo "Could not successfully run query ($sqlS) from DB: ".mysql_error();
		exit;
	}

while($row = mysql_fetch_assoc($resS))
{
	echo $row["Year_Name"]."<br>";
}
```

---

### Post by ladjack on 2008-05-26
Clean reinstallation just helps.

---

