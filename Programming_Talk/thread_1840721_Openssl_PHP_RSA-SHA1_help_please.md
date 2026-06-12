---
title: "Openssl PHP RSA-SHA1 help please"
date: 2011-09-08
forum: Programming Talk
---

### Post by dazman19 on 2011-09-08
Hi,

I am having some problems with Open SSL. We are using an API provided to us, but the SSL key generation is too complicated for some of the technicians when a new site is set up, so i have created a button which generates and loads in the SSL keys. (which works great when i create the keys using OPENSSL at the command line)

The API manual states:
1) Only messages signed using RSA-SHA1 will be accepted.
The RSA-SHA1 signature method uses the RSASSA-PKCS1-v1_5 signature algorithm as defined in [RFC3447] section 8.2 (more simply known as PKCS#1), using SHA-1 as the hash function for EMSA-PKCS1-v1_5. It is assumed that the Consumer has provided its RSA public key in a verified way to the Service Provider, in a manner which is beyond the scope of this specification. 

And when I create openssl keys using this command line the keys work:
```

$ openssl genrsa -out privatekey.pem 1024
$openssl req -newkey rsa:1024 -x509 -key privatekey.pem -out publickey.cer -days 365
# answer a number of questions
$ openssl pkcs12 -export -out public_privatekey.pfx -inkey privatekey.pem -in publickey.cer

```

The keys generated this way look like this and they work with the API:
```

$ cat privatekey.pem
-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQCsqTvyRWn26eDyKD1NBd2sWO4cw7YZ2EGgXduV/j9ecWlRFmXz
YzU5AahZc94k5ZFYyMD6fv8DJV2t8l5QPc1guNmjnRqZXn4lcnT5N1rmpx6BF/11
tN4XeUV27v3A8zvQDCsIooMRDAQENVxW3CwjytuouE/QgWs4T2CjL2jW1QIDAQAB
AoGAWJA1/387aztr9spNJ0Tq/4xeFsMMlRUoFGoQSE+xkW/65WznvoAUvLjs8XVN
bP+UHkZbNiIODD8OXjsDxYTt4ucYIDkSio+z50FvJookFsM2T7BQOjLH2TfkEmQ9
TkNZ9IuH4GGFYfu5I4wNaAo1KHDJdyWDykAZuFeTS7YFWAECQQDaWtZDdkOltzuN
7eovl2Q1u6MDsoAgML4L3D33rj8Tjz0nsgnCYMW4yrPJbw41OvemPh/v9kvz7KaT
qqtL/dH1AkEAym2wGQrHwNShHAp4epWRAkjFLA22UcSH2lzWc1pVJqXvFrNkLjGe
yByvi1sojGaczlVXMuHdtwOPxhnbjIiFYQJBAIQWoTjsKN3taxRfkOQ7Q76RhHpv
F7zhX4XTNJVJDhUp+Ee0Ft1EJzezP3EiQkkHI9qoCC/kIWwsg1Qe0ULGB6UCQEAk
99tHljqdZhv7mWfGwzeFFa26/p30d9QS/QV6h2cCx7taxxD4OkdRB7NSBIxQ67la
Q5JlDhuzLjjo8rAahqECQF0wNq7a7k+Z3vOHDGBJFNWrMEFsNX4DlW2V9QZUg52/
wN47b0K9BFBn1Jsr+nEJ1jopIqbrj6synEqCSAaJ7Ig=
-----END RSA PRIVATE KEY-----

```

However when i generate the keys with PHP's OPEN SSL they look different and I cant find much info on the php website on how to change the RSA settings.

But the private key has this garbage at the top and i dont know how to  get rid of it and i think it is making my keys incompatible with the API i am using. 
```

$ cat privatekey.pem
-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: DES-EDE3-CBC,EA95F56908D2F888

YN0x9LKiPv7I+ikMbS470kGGn02wHJxHYpbqVQuDzvxcjtp2/X9IxKV9m8dqpXd0
eF4oLpghU3sPjhqohh8W+DwOvTGbPI+P+kaHoH61JJ1H0OF8qoPtgEbWI6lhL33N
jNFC+1rALXWLT5kBOK78WgmPUmR71Rdw27Sqqaba1HIkLnUReLQzFKKS0PtQV17t
aMEVKRdwbvVXPQdjrFUFyM53A8L+QNK6AC6m1kzAAAV2gKFMQmTy5NMgI81+QUqC
i/rvjgX39wTHWuRp0wbeJS4cUpgTMbG417k++cGwP/LlrF59QvXoJ+KxW9RMw9wT
0I7nGZl4MH32Hb2IAQ1G66hTBg9mLu8YBeiOb07W4T2bWE9XpPu8ZHnf/lcbgLaV
3Bf8ye4ClwS9YSMCvgpdDT3XROysqD41uhSXrfBPOYEhI6Xfo3s9ifKbCLtZFC3e
A0Vs5Wti89D40PbjrBDrbwniRWMDVU/Ul62EVMLemh8x8KGPNhb/C1b4xjlXcODG
vvmadH0mGkf1nQxOnLl+E89jOfWAH4mU0rFpMleo3qMjNpTnkuT/FJHawnGhzFb/
nbvrSDIX+gB0ab+QJOlFx5PpZgd5u5hONT1ram8Hvc74L2TCjCIlPCsTXyqlFUNV
xj33t+5ifFBr0isthnP6pDMhBTO2T1lNA8o8bU33MwpELDGCYzhpiYMHg470T6rY
yqgfdLOGN4OlVTg6BoEPc/+cVHmbg8jds/fUM/BOJ7mI61uIJEpxyZC+2fO9t56W
0ZLLmlshfPvxyrt14rLfapj4qgOBhIwFI4aqhACs3YnKZhLZGSP+gA==
-----END RSA PRIVATE KEY-----

```

Obviously i dont know an awful lot about openssl but i do have a basic understanding of how the RSA algorithim works.

Here is my PHP code I wrote to generate the public/private keys:

[PHP]


/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 * @author Daryl Blake
 */

class SSLKey {
    //requires OPEN-SSL PHP openssl
    
    private $_keyname;
    private $_keysize = 1024;
    private $_password;
    private $_publickey;
    private $_privatekey;
    private $_days = 365;
    private $_csrcert;
    
    
    public function __construct($options = array())
    {
        if(isset($options['keysize']) && intval($options['keysize']) >= 32)
        {
            $this->_keysize = intval($options['keysize']);
        }
        if(isset($options['password']))
        {
            $this->_password = $options['password'];
        }
        if(isset($options['keyname']))
        {
            $this->_keyname = $options['keyname'];
        }
        if(isset($options['days']))
        {
            $this->_days = $options['days'];
        }
    }
    
    public function generateKeys() // .key file
    {
        if(!isset($this->_keyname))
        {
            throw new Exception("No Key Name Specified");
        } 
        // DATA (YOU CAN CHANGE THIS)
        $dn= array(
            "countryName" => "NZ",
            "stateOrProvinceName" => Settings::getCity(),
            "localityName" => Settings::getCity(), 
            "organizationName" => Setting::getBusinessName(), 
            "organizationalUnitName" => Setting::getSiteType(), 
            "commonName" => Setting::getBusinessName(), 
            "emailAddress" => Setting::getFromEmail()
        );
        // CONFIG
        $configargs = array(
            'x509_extensions' => 'v3_ca',
            'private_key_bits' => $this->_keysize,
            'private_key_type' => OPENSSL_KEYTYPE_RSA,
        );
        $privkey = openssl_pkey_new();
        $csr = openssl_csr_new($dn, $privkey, $configargs);
        $sscert = openssl_csr_sign($csr, null, $privkey, $this->_days);
        openssl_x509_export($sscert, $this->_publickey);
        openssl_pkey_export($privkey, $this->_privatekey, $this->_password);
        openssl_csr_export($csr, $this->_csrcert);
    }
    public function getPublicKey($filelocation = "")
    {
        if($filelocation)
        {
            return file_put_contents($filelocation, $this->_publickey);
        } 
        else 
        {
            return $this->_publickey;
        }
    }
    public function getPrivateKey($filelocation = "")
    {
        if($filelocation)
        {
            return file_put_contents($filelocation, $this->_privatekey);
        } 
        else 
        {
            return $this->_privatekey;
        }
    }    
    public function getCertificate($filelocation = "")
    {
        if($filelocation)
        {
            return file_put_contents($filelocation, $this->_csrcert);
        } 
        else 
        {
            return $this->_csrcert;
        }
    }    
}

//in my code after the class in included... 
$keydata = array(
    "keysize" => 1024,
    "password" => "test123",
    "keyname" => "testkey",
    "days" => 365
);

$sslkeygen = new SSLKey($keydata);

$sslkeygen->generateKeys();


$sslkeygen->getPublicKey("xero.cer");
$sslkeygen->getPrivateKey("xero.key");

[/PHP]

(I am using a LAMP environment AKA Linux/Apache/PHP/MySQL) 
all my development is done in ubuntu or debian with php 5.3+

---

### Post by dazman19 on 2011-09-09
Does anyone know how to generate a public key and private key with RSA-SHA1 using the PHP open SSL library ?

---

### Post by dazman19 on 2011-09-28
I have written a program which creates these correctly. Contact me if you need a copy.

---

