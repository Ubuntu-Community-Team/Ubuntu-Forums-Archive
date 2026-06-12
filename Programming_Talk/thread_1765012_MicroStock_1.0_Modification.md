---
title: "MicroStock 1.0 Modification"
date: 2011-05-22
forum: Programming Talk
---

### Post by chief30 on 2011-05-22
```
<?php

function getStockSite($stockLink){
   
   if ($fp = fopen($stockLink, 'r')) {
      $content = '';
        
      while ($line = fread($fp, 1024)) {
         $content .= $line;
      }
   }

   return $content;  
}

function processStockSite($wurl){
    
    $wrss = getStockSite($wurl);
    $name  = '-';
    $price = '';
    $diff  = '';
    
    if (strlen($wrss)>100){
        $spos = 0;
        
        // Get text
        $spos = strpos($wrss,'</span>:',$spos)+3;
        $spos = strpos($wrss,'<big>',$spos);
        $epos = strpos($wrss,'</div><h1>',$spos);
        if ($epos>$spos){
           $text = substr($wrss,$spos,$epos-$spos);
        } else {
           $text = '-';
        }

        $spos = $epos + 10;
        // Get company name
        $epos = strpos($wrss,'<',$spos);
        if ($epos>$spos){
            $name = substr($wrss,$spos,$epos-$spos);
        } 

        
        // Get actual price
        $spos = strpos($wrss,'yfs_l10')+strlen('yfs_l10');
        $spos = strpos($wrss,'>',$spos)+1;
        $epos = strpos($wrss,'<',$spos);
        if ($epos>$spos){
            $price = substr($wrss,$spos,$epos-$spos);
        } else {
            $price = '-';
        }
        
        // Get direction
        $spos = strpos($wrss,'alt',$epos)+strlen('alt')+2;
        $epos = strpos($wrss,'"',$spos);
        if ($epos>$spos){
            $dir = strtolower(substr($wrss,$spos,$epos-$spos));
        } 
        
        // Get difference
        $spos = strpos($wrss,'>',$epos+3)+1;
        $epos = strpos($wrss,'<',$spos);
        if ($epos>$spos){
            $diff = substr($wrss,$spos,$epos-$spos);
        } 

    }
    
    $result['name']  = $name;
    $result['value'] = $price;
    $result['diff']  = $diff;
    $result['direction'] = $dir;
    $result['text']  = $text;
    
    return $result;
    
}


// Get stock data
//$data = processStockSite('c:\q.htm'); // Google
$data = processStockSite('http://finance.yahoo.com/q?s=GOOG'); // Google
//$data = processStockSite('http://finance.yahoo.com/q?s=MSFT'); // Microsoft
//$data = processStockSite('http://finance.yahoo.com/q?s=AAPL'); // Apple
//$data = processStockSite('http://finance.yahoo.com/q?s=GE'); // GE
?>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "DTD/xhtml1-transitional.dtd">
<html>
<head>
   <title>Micro Stock</title>
   <link href="style/style.css" rel="stylesheet" type="text/css" />
</head>
<body>
    <div id="main">
      <div id="caption"><?php echo $data['name']; ?></div>
      <div id="icon2">&nbsp;</div>
      <div id="result">$<?php 
         echo $data['text'];
         //echo $data['value'].' ';
         //if ($data['direction'] == 'up') echo '<span class="up"> +'.$data['diff'].'</span>';
         //else echo '<span class="down"> -'.$data['diff'].'</span>'; ?>
      </div>
      <div id="source">Micro Stock 1.1</div>
    </div>
</body>   

```


As you can see form above, this is the script I would like to change up but not really sure where to start.  The script works just fine but will only show one ticker at a time.  I would like to be able to show multiple either horizontally or vertically.  I tried a couple of different things to the code but they only caused it not to work.  Any help would be greatly appreciated!! Thanks!

---

