---
title: "More PHP uploader problems..."
date: 2010-03-09
forum: Programming Talk
---

### Post by Crafty Kisses on 2010-03-09
Ok so, let me tell you everything that I have, I'm getting fairly frustrated because I can't get this huge feature of our new website to work which is users uploading vidoes/images to our site, and I've been trying for ages, now mind you I'm very new to PHP. So we currently use **name.com** as our hosting service, I have the following PEAR packages installed so I can get this uploader to work:

```
HTML_Javascript  	1.1.2  	 
HTML_Progress 	1.2.6 	
HTML_Progress2 	2.4.1 	
HTML_QuickForm 	3.2.11 	
HTML_QuickForm_Controller 	1.0.10 	
HTML_QuickForm_DHTMLRulesTableless 	0.3.3 	
HTML_QuickForm_Renderer_Tableless 	0.6.1 	 
HTML_QuickForm_Rule_Spelling 	0.2.0 	
HTML_QuickForm_SelectFilter 	1.0.0RC1 
HTML_QuickForm_advmultiselect 	1.5.1 	
HTML_QuickForm_altselect
```
Those are the current PEAR modules installed according to cPanel. So here's the current script I'm using:
[PHP]
 <?php
   
      require_once 'HTML/QuickForm.php';
  
       
  
      function myProcess($values)
 
      {
  
          global $form;
  
          $destination = './upload/';

       
 
          $file =& $form->getElement('tstUpload');
  
          if ($file->isUploadedFile()) {
 
              $ok = $file->moveUploadedFile($destination);
 
       
 
              if ($ok) {

                  // write the semaphore to tell progress meter to stop

                  // in script 'progressbar.php'

       

                  $fp = fopen($destination . $_GET['ID'],'w',false);
 
                  fwrite($fp, 'done');
  
                  fclose($fp);
 
              }
  
          }

      }
 
      ?>

      <html>

      <head>
 
      <script language="javascript">
 
      <!--
 
      function DoUpload() {
 
        theUniqueID = (new Date()).getTime() % 1000000000;
  
        parent.meter.window.location = "progressbar.php?ID=" + theUniqueID;
 
        parent.files.selfref.action = "formselfref.php?ID=" + theUniqueID;
 
        parent.files.selfref.submit();
  
      }
 
      //-->
  
      </script>
  
      </head>
 
      <body>
  
      <?php
 
       
  
      $form =& new HTML_QuickForm('selfref');
 
       
 
      // We need an additional label below the element
  
      $renderer =& $form->defaultRenderer();
 
      $renderer->setElementTemplate(<<<EOT
  
      <tr>
  
          <td align="right" valign="top" nowrap="nowrap"><!-- BEGIN required --><span style="color: #ff0000">*</span><!-- END required --><b>{label}</b></td>
  
          <td valign="top" align="left">
  
              <!-- BEGIN error --><span style="color: #ff0000">{error}</span><br /><!-- END error -->{element}
  
              <!-- BEGIN label_2 --><br/><span style="font-size: 80%">{label_2}</span><!-- END label_2 -->
  
          </td>
 
      </tr>
  
       
 
      EOT
  
      );
  
       
  
      $form->addElement('header', null, 'Uploaded file rules');
  
      $form->addElement('file', 'tstUpload', array('Upload file:', 'Rule types: \'uploadedfile\''));
  
     $form->addRule('tstUpload', 'Upload is required', 'uploadedfile');
  
       
  
      $form->addElement('header', null, 'Submit the form');
  
      $submit[] =& $form->createElement('button', null, 'Upload', array('onClick'=>'DoUpload();'));
  
      $form->addGroup($submit, null, null, '&nbsp;', false);
  
       
  
      $form->applyFilter('__ALL__', 'trim');
  
       
  
      if ($form->validate()) {
  
        
  
          $form->freeze();
  
          $form->process('myProcess', true);
  
          echo '<p>&lt;&lt; <a target="_top" href="../index.html">Back examples TOC</a></p>';
  
       
  
      } elseif (isset($_GET['ID'])) {
  
          $destination = './uploads/';
  
          $fp = fopen($destination . $_GET['ID'],'w',false);
 
          fwrite($fp, 'error');
  
          fclose($fp);
  
      }
  
      $form->display();
  
      ?>
  
      </body>
  
      </html>[/php]
Now mind you this is from a QuickForm tutorial, and I have tried countless other scripts, that tend to fail, that leave me at a blank page, and give me upload errors. So now that we have that out of the way, I also am aware that comes with a progress bar, and I tried to upload that as well, and still it wouldn't work, just a blank white screen. I just don't know what I'm doing wrong. This is how our directory structure is setup, we have a public_html directory, that's where all of our files go, then we have a root directory, which some files go there, but not many. So what I'm asking is maybe step by step instructions? I've just been trying for so long to get this to work, it's just not working.

---

### Post by CyberJack on 2010-03-11
A blank white screen normally means you have one or more errors which are not shown due to php.ini settings. If error logging is enabled in php.ini you can check your webserver (apache) logs for errors. They might help you solve the problem.

One other thing to look at is the size of the video/photo which you are uploading. If it's bigger than the maximum size allowed in php.ini it will trigger an error.

Also make sure your upload directory is writable by the webserver.

---

