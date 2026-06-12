---
title: "[SOLVED] Ajax Problems"
date: 2007-12-13
forum: Programming Talk
---

### Post by cerealtx on 2007-12-13
i CAN NOT FIND anythign wrong 4 the life of me!!!! and i need it for my company website, anyone see anything wrong? am i doing the option wrong with the element ID?```
     <script language="javascript" type="text/javascript">
      <!--
      function getHTTPObject(){
      if (window.ActiveXObject) return new ActiveXObject("Microsoft.XMLHTTP");
      else if (window.XMLHttpRequest) return new XMLHttpRequest();
      else {
      alert("Your browser does not support AJAX.");
      return null;
      }
      }
      function setOutput(){
      if(httpObject.readyState == 4){
      document.getElementById('showpackage').value = httpObject.responseText;
      }       
      }
      function doWork(){
      httpObject = getHTTPObject();
      if (httpObject != null) {

      httpObject.open("GET", "getpackage.php?package="
      +document.getElementById('inputpackage').value, true);
      httpObject.send(null);
      httpObject.onreadystatechange = setOutput;
      }
      }
      var httpObject = null;
      //-->
      </script>

              <select name="package" id="inputpackage" onchange="doWork();">
              <option value="Personal">Personal
              <option value="Business">Business
	      <option value="Professional">Professional
	      <option value="Reseller">Reseller
              </select>
	<div id="showpackage"><b>Package Info.</b></div>
```

getpackage.php
```
<?php

if (isset($_GET['package'])
{
switch($_GET['package'])
{
      case Personal:
      echo '<p><u>Personal</u>';
		break;
       case Business:
         echo '<p><u>Business</u>';
      break;
      case Professional:
      echo '<p><u>Professional</u>';
      break;
      case Reseller:
      echo ' <p><u>Reseller</u><br>';
      break;
     default:
     echo 'error';
     break;
  
      }
	}

      }

      ?>
```

---

### Post by cerealtx on 2007-12-13
think i found another problem, i needed the Form in there but still nothing :( ```
             <form action="doWork();">
              <select name="package" id="inputpackage">
              <option value="Personal">Personal
              <option value="Business">Business
	      <option value="Professional">Professional
	      <option value="Reseller">Reseller
              </select>
	      </form>
```

---

