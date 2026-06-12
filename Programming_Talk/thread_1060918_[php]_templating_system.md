---
title: "[php] templating system"
date: 2009-02-05
forum: Programming Talk
---

### Post by ELD on 2009-02-05
Basically i am creating a templating system where the templates are html files with some variables in them like "$username" etc etc.

I am wondering in the class's function that actually brings the template in i will have to global every single variable that the templates could possible use, which seems stupid, is there any other way around it?

The only way around it that i can think of is instead of replacing the "$username" directly, have a string replace before the template is loaded changing say "{username}" in a template to what "$username" is, but is that not a huge load of resources?

For reference current class implementation (which currently won't work properly as i will have to global anything templates may use, argh!).
[php]
class templating
{
	// where the template files are kept (e.g ./templates/utopia)
	var $path;
	
	function set_path($path_wanted)
	{
		// first we need to check the template is actually there
		if($this->template_exists($path_wanted) == true)
		{
			$this->path = $path_wanted;
		}
		
		// else check to make sure utopia the defualt template is there so we can revert to that
		else
		{
			if($this->template_exists(PXB_ROOT.'templates/utopia/') == true)
			{
				$this->path = PXB_ROOT.'templates/utopia';
			}
			
			else
			{
				error_message('No template was available for use, check template folder exists if not please re-upload.');
			}
		}
	}
	
	function template_exists($template)
	{
		if (is_dir($template.'/') == true)
		{
			return true;
		}
		
		else
		{
			return false;
		}
	}
	
	function template_file_exists($template_file)
	{
		if (file_exists("{$this->path}/{$template_file}.html"))
		{
			return true;
		}
		
		else
		{
			return false;
		}
	}
	
	function load_template($file, $block='')
	{			
		$actual_file = $this->path . '/' . $file . '.html';
		
		// okay now check the template file is there and bring it in
		if($this->template_file_exists($file) == true)
		{
			if (empty($block))
			{
				$t = file_get_contents($actual_file);
				echo eval("<<<TMP\r\n".$t."\r\nTMP;\r\n");
			}
			
			else
			{
				$t = file_get_contents($actual_file);
	
				$pattern = '#\[block:\s*(' . $block . ')\](.*)\[/block:\s*(\1)\]#is';
	
				// find the wanted part of the template
				preg_match($pattern, $t, $matches);
	
				// return the contents to be evaled and echod out
				echo eval("<<<TMP\r\n".$matches[2]."\r\nTMP;\r\n");
			}
		}
		
		else
		{
			error_message("template {$file}.php file not available<br />
			{$this->path}");
		}
	}
}
[/php]

---

### Post by Reiger on 2009-02-05
There are a few ways. First you can use straightforward search/replace patterns. That works well if it's just constants you need. You may want to consider a template_data object which acts as a 'door' (container) object to your data.

Alternatively you can use a basic XML format for data and 'inflate' it to the (X)HTML you need, defining the template by means of XSLT or specific PHP functions.

A 3rd way is -if you need to call functions or include specific scripts- to use a specific XML tag which encapsulates everything required for this specific PHP code and map that to an include/system/shell_exec statement at run time.

Finally, nothing is to stop you from rewriting your template as a PHP script consisting of a series of echo/print statements! All you actually need to do then is to compute the include at run time.

---

