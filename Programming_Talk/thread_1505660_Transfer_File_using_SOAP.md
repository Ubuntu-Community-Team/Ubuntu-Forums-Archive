---
title: "Transfer File using SOAP"
date: 2010-06-09
forum: Programming Talk
---

### Post by Black Mage on 2010-06-09
Hey,

I am having this problem transferring files using NuSOAP. I understand that you can read a file and transfer it has a string but its not working. Here is an example

Client:

    ```

    require('libraries/nusoap/nusoap.php');
    $url = "http://www.example.com";
     
    $client = new nusoap_client($url);
    args = array('file_name' => 'myfile.zip');
    $return = $client->call('getFile', array($args));
    
    if(empty($return){
        echo "WHY IN THE WORLD IS THIS EMPTY!!!!!";
    }

```


Server:

    ```

    require('libraries/nusoap/nusoap.php');
    $server = new nusoap_server;
     
    $server->configureWSDL('server', 'urn:server');
     
    $server->wsdl->schemaTargetNamespace = 'urn:server';
    
    $server->register('getFile',
    			array('value' => 'xsd:string'),
    			array('return' => 'xsd:string'),
    			'urn:server',
    			'urn:server#getFile');
    
    function getFile($value){
    
    $returnData= "";
    $filePath=value['file_path']
    $mode="r";
    	
    		if (floatval(phpversion()) >= 4.3) {
    	        $returnData= file_get_contents($filePath);
    	    } else {
    	        if (!file_exists($filePath)){ 
    	        	return -3;
    	        }
    	        
    	        $handler = fopen($filePath, $mode);
    	        if (!$handler){ 
    	        	return -2;
    	        }
    	
    	        $returnData= "";
    	        while(!feof($handler)){
    	            $returnData.= fread($handler, filesize($filePath));
    	        }//end  while
    	        
    	        fclose($handler);
    	    }//end else
    	    
    
    return $returnData;
    
    }

```


Here is the really strange part. If I return the file name, or fize size or something like that, it will work. It will just not return the file itself. Help please.

---

