---
title: "Can I pass a PDO object? in PHP?"
date: 2008-06-18
forum: Programming Talk
---

### Post by thenetduck on 2008-06-18
Hi 
I made a class that works like my connection script. I would like to have a "getPDO" method in the class that returns the PDO object. (well I did do that) and I to use use that object with ->execute() but says it can't find that method... for instance I did something like this 
```

include 'connect2DB.php';
$conn = new connect2DB();
$thePDO = $conn->getPDO();
$thePDO->prepare('SELECT * FROM ?);
$thePDO->execute(array('users'));

```

it knows about the prepare method apparently but  I would like to use the execute method. In the  connect2DB class.. this is how I return the PDO object. 

```


function __construct()
    {
          // Creates a connection to the database
         try{
            //$connection = new PDO($info,$user,$pass);
            $this->connection = new PDO($this->dsn, $this->user,$this->pass);
        } catch (PDOException $e)
        {
            echo 'Connection failed: ' . $e->getMessage();
       }
    }

   /* This function returns the PDO so other classes
   * can use it.
   */ 
   public function getPDO()
   {
        return $this->connection;
   }  



```

I have all the correct connection information set up... 

Anyone know what I am doing wrong? 

The Net duck

---

### Post by thenetduck on 2008-06-18
LOl Ok I think I know now.. 
I was tryin to "execute" the PDO... .but you need to execute a PDO Statment not the object :) ...

---

