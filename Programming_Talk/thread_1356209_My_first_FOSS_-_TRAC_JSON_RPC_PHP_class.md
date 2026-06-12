---
title: "My first FOSS - TRAC JSON RPC PHP class"
date: 2009-12-15
forum: Programming Talk
---

### Post by brian183 on 2009-12-15
Hi everyone, I've been a programmer for about 10 years now but I've never made anything I've written freely available.  I found some time to write up a simple PHP class that executes RPC commands to a server that hosts a TRAC server and has the RCP plugin installed for it.

Here's the git repository [http://github.com/Brian183/TRAC-JSON-RPC-PHP-class]("http://github.com/Brian183/TRAC-JSON-RPC-PHP-class")

TRAC is a popular issue tracking system that integrates with subversion. I'm sure everyone here is aware of it. My class contains methods which executes an RPC command and parses the result into a php variable.  Currently it uses JSON to execute all the commands. Also, multiple RPC calls is available using this class (see usage).

I've not implemented this class in any project and have not tested all methods. It also does not have any methods for the wiki yet but that will come along shortly.

Let me know what you think or if you find issues.  Any issue you find please put them in the github.

Thank you and I hope you like it.

-brian

---

### Post by Hellkeepa on 2009-12-16
HELLo!

After a quick look at it, it seems really well written. Only two minor issues, so far:
[list=1][*]Duplicated this bit of code:
```

if(! function_exists('json_decode') AND class_exists('Services_JSON') === TRUE) {
	function json_decode($json)
	{
		$json = new Services_JSON(SERVICES_JSON_SUPPRESS_ERRORS);
		return $json->decode($json);
	}
}
```
[*]Some header comments for the methods could have been a bit better, for instance "get_ticket()" and "get_attachments()" both read "Get ticket".[/list]
Minor issues, as I said. ;-) Other than that, really nice work. This is the kind of code one should see more often.

Happy codin'!

---

### Post by brian183 on 2009-12-16
1. Ahh Good catch.  Kinda need that function argument so it can actually decode json.

2. Yeah I'll be writing better commenting soon.  Version 1.02 will have methods for the wiki RPC and better commenting along with it.


Thanks for taking a look.

---

