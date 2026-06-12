---
title: "PHP Mailer SMTP Authentication"
date: 2010-12-23
forum: Programming Talk
---

### Post by dazman19 on 2010-12-23
Hi, I am trying to send an email using SMTP authentication.

The code works MINT! for when $setting_smtpauth is set to 0. But when I set it to 1 and define the following:

$setting_smtpuser = mailer
$setting_smtppass = Password123

it does NOT work. I have spent ages on this. And done VAR dumps and everything and the password and username is there.
I have even tried base64_encoding the username and password.

I know the password and username are correct because: 

Helo
500 5.3.3 Unrecognized command
helo
250 somefrickinawesomemailserver.com Hello [192.168.37.117]
AUTH LOGIN
334 VXNlcm5hbWU6
bWFpbGVy
334 UGFzc3dvcmQ6
UGFzc3dvcmQxMjM=
235 2.7.0 Authentication successful
451 4.7.0 Timeout waiting for client input


Connection to host lost.

SOOO.... 

It must be something to do with this piece of code here:
[PHP]if($setting_smtpauth==1)
            {
                    $mail->SMTPAuth=true;
                    $mail->Username=$setting_smtpuser;
                    $mail->Password=$setting_smtppass;
                    $mail->Timeout = 30;
            }[/PHP]

But I dont know why it wont work. Any ideas?
[PHP]
 $mail=new PHPMailer();
            $mail->SetLanguage('en');
            $mail->IsSMTP();
            $mail->Host=$setting_smtpserver;

            if($setting_smtpauth==1)
            {
                    $mail->SMTPAuth=true;
                    $mail->Username=$setting_smtpuser;
                    $mail->Password=$setting_smtppass;
                    $mail->Timeout = 30;
            }

            if($logged_useremail!="")
            {
                $mail->From=$logged_useremail;
                $mail->FromName="$logged_username - $setting_businessname";
                $mail->Sender=$logged_useremail;
            }
            else
            {
                $mail->From=$setting_fromemail;
                $mail->FromName=$setting_businessname;
                $mail->Sender=$setting_fromemail;
            }

            if((intval($setting_developmentmode)==0) && (intval($setting_demomode)==0)) //IF NOT DEVELOPMENT MODE
            {
                    $addrs=0;
                    foreach ($destinations as $key => $value)
                    {
                            if( !($key || $value) )
                            {
                                throw new Exception("You cannot have an empty destination");
                            }
                            if(trim($key)) {
                                    if(!strstr($value,"@") && !strstr($key,"@") && $setting_faxfrom) {
                                            $key=str_replace(" ","",$key)."@fax.2talk.co.nz";
                                            $mail->From=$setting_faxfrom;
                                            $fax=true;
                                            $mail->AddAddress($key, $value);
                                            $addrs++;
                                    }
                                    else {
                                            if(strstr($key,";")) {
                                                    $dests=explode(";",$key);
                                                    foreach($dests as $dv) {
                                                            if($dv!="") {
                                                                    $mail->AddAddress(trim($dv));
                                                                    $addrs++;
                                                            }
                                                    }
                                            }
                                            else {
                                                    $mail->AddAddress($key, $value);
                                                    $addrs++;
                                            }
                                            $fax=false;
                                    }
                            }
                    }
                    foreach($extraArgs["bccaddresses"] as $namedestination) 
                    {
                        if($namedestination)
                        {
                            $mail->AddBCC($namedestination);
                            $bccAdded=true;
                        }
                    }
                    if(!$bccAdded)
                    {
                        $mail->AddBCC($setting_statusemail);
                    }
                    if($setting_reporthome) {
                            $mail->AddBCC('status@ezyvet.com');
                    }

//                    if($cc) { // originally to stop performance summary report going to status@ for each person
//                            $mail->AddBCC($setting_statusemail, $setting_statusemail);
//                    }
//
//                    if(!$destinations[$setting_statusemail] && $setting_statusemail && !$options["dontstatussend"]) {
//                        $mail->AddBCC($setting_statusemail, $setting_statusemail);
//                        $addrs++;
//                    }
                    
                    

                    if($addrs==0) {
                            errorlog("Error: Email has no-one to send to");
                            return true;
                    }//No one to sent to

            }
            else                    //IF in DEVELOPMENT MODE
            {
                debug(print_r($extraArgs));

                    foreach ($extraArgs["bccaddresses"] as $namedestination)
                    {
                        if($namedestination)
                        {
                            $mail->AddBCC($namedestination);
                        }
                    }

                    foreach ($destinations as $key => $value)
                    {
                            if(!$IN_CRON_TASK){if($key!=""){debug("AddAddress($key, $value)");}}
                    }
            
                    if(!$IN_CRON_TASK){debug("AddAddress($setting_fromemail, $setting_fromname)");}
                    if(strstr($setting_fromemail,";")) {
                            $dests=explode(";",$setting_fromemail);
                            foreach($dests as $dv) {
                                    if($dv!="") {
                                            $mail->AddAddress(trim($dv));
                                            $addrs++;
                                    }
                            }
                    }
                    else {
                            $mail->AddAddress($setting_fromemail, $setting_fromname);
                            $addrs++;
                    }
            }

            for($i=0; $i<count($extraArgs["attachments"]); $i++)
            {
                    if(preg_match("/files\/".$setting_uid."\/attachments\//", $extraArgs["attachments"][$i])) {
                            $file_id = str_replace('files/'.$setting_uid.'/attachments/', '', $extraArgs["attachments"][$i]);
                            extract(query_item("SELECT file_name FROM files WHERE file_id='$file_id'"));
                            $mail->AddAttachment($extraArgs["attachments"][$i], $file_name);
                    }
                    else {
                            $mail->AddAttachment($extraArgs["attachments"][$i]);
                    }
            }

            for($i=0; $i<count($extraArgs["embeddedImages"]); $i++)
            {
                    $mail->AddEmbeddedImage($extraArgs["embeddedImages"][$i][0], $extraArgs["embeddedImages"][$i][1], $extraArgs["embeddedImages"][$i][2]);
            }

            $mail->Body=$contents;
            $mail->Subject=$subject;


            $mail->AltBody=$extraArgs["altcontents"];
            if(!$fax)
            {
                    $mail->Subject=$subject;
            }
            else
            {
                    $mail->Subject="fax";
            }

            if($extraArgs["isHTML"]){$mail->IsHTML(true);}else{$mail->IsHTML(false);}
            
            if ($mail->Send())
            {
                    if( $setting_sendnotifiers && ( count($extraArgs["attachments"]) || count($extraArgs["embeddedImages"]) ) )
                    {
                            if(!$fax)
                            {
                                     EmailStuff::send_notifier($destinations, $mail);
                            }
                    }
                    return true;
            }
            else
            {
                    echo("<script>top.msg('There was an error! $mail->ErrorInfo',0,'error');</script>");
                    return false;
            }
    }

[/PHP]

---

### Post by AlexanderDGreat on 2011-07-17
Is it in your server configuration or ISP? I'm having the same problem, with Thunderbird, I'm using SMTP auth no problem, but using it with PHPMailer is so not working!

Any updates on this?

---

