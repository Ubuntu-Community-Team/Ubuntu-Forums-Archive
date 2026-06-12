---
title: "Subversion scripts"
date: 2009-03-31
forum: Programming Talk
---

### Post by hessiess on 2009-03-31
While looking for a solution to the problem of easily adding and removing files automatically form an SVN repo I came across these commands:

```

svn status | awk '/^?/ {print $2}' | xargs svn add
svn status | awk '/^!/ {print $2}' | xargs svn remove

```

While these work prefectilly if there are no spaces in the file names, they fail if there are spaces. What would I need to do to make it support spaces, and also add the possibility of excluding files and directories?

Thanks.

---

### Post by hessiess on 2009-03-31
Wrote a PHP script that partially solves the problem, still lacks the option of excluding files or directories.

[PHP]
<?php
    $status = shell_exec  ("svn status");
    $status_line = split("\n", $status);

    $svn_dif = array();
    foreach($status_line as $line)
    {
        $line_chars = str_split($line);
	$key = array_shift($line_chars);

	$out = "";
	$bigin = 0;

        foreach($line_chars as $char)
        {
	    if($bigin == 1 && $char == " ")
	    {
	        $out .= "\\" . $char;
	    }

	    else if($bigin == 1)
	    {
	        $out .= $char;
	    }

	    if($char != " " && $bigin == 0)
	    {
	        $out .= $char;
	        $bigin = 1;
	    }
	}
	array_push($svn_dif, array('key' => $key, 'file' => $out));
    }

    print_r($svn_dif);

// loop over array and generate nesoserry SVN commands.
    $addcmd = "svn add ";
    $delcmd = "svn remove ";

    foreach($svn_dif as $element)
    {
        if($element['key'] == '?')
	{
	    $addcmd .= $element['file'] . " ";
	}

        if($element['key'] == '!')
	{
	    $delcmd .= $element['file'] . " ";
	}
    }

    print $addcmd . "\n";
    shell_exec($addcmd);

    print $delcmd . "\n";
    shell_exec($delcmd);
[/PHP]

---

