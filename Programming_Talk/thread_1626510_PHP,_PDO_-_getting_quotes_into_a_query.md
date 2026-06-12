---
title: "PHP, PDO - getting quotes into a query?"
date: 2010-11-20
forum: Programming Talk
---

### Post by meastwood on 2010-11-20
I have a mysql query defined in a .ini file.  The query uses a php named placeholder  (:invoice) that needs to be quoted - I cannot get them quoted.  Am new to php - would appreciate some help.

Using mysql 5.075, PHP 5.2.6-3ubuntu4.6 with Suhosin-Patch 0.9.6.2 (cli).  magic quotes are enabled.

Query in .ini file:
```
d1=select invoiceitems.inv_ref, invoices.inv_date, item_number, prod_id, item_unit_cost, item_qty, "("item_unit_cost "*" item_qty")" from invoiceitems inner join invoices on invoiceitems.inv_ref "=" invoices.inv_ref where invoiceitems.inv_ref IN "(":invoice")" 
```

:invoice needs to be replaced with something like -
"inv00001"
"inv00001","inv00002","inv00005"          (any number and combination of invoices - each one quoted)

Code that extracts a list of invoices 
```

   ....
   $shopact=$_POST["shopact"];
   if ($_POST["submitted"] == "jscript") $js=True;
   $strlist=implode(",", $shopact);
   $qry = $strlist == "All invoices" ? "d2" : "d1";
   if ($qry == "d1") {
      $strlist="\"" . str_replace(",", "\",\"", $strlist) . "\"";
      $results=getData($iniFile, "demo2", "d1", $params=True, $vals=$strlist);
      }
   else {
      $results=getData($iniFile, "demo2", "d2");
   }
```

Function to retrieve DB values
```
function getData($ini, $dbinst, $qry, $params=False, $vals="") {
   $dbdata=new ArrayObject();
   $conn=new DemoPDO($ini);                                         // Instaniate an instance
   //$conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
   if ($params) {
      $stmt=$conn->prepare($conn->getQuery($dbinst,$qry));
      $stmt->bindParam(':invoice', $vals, PDO::PARAM_STR))
      $stmt->execute();
      $dbdata=$stmt->fetchAll();
      }
   else {
      $stmt=$conn->runQuery($dbinst, $qry);   
      $stmt->setFetchMode(PDO::FETCH_NAMED); 
      while ($row = $stmt->fetch()) $dbdata->append($row);
      }
   $stmt->closeCursor();
   return $dbdata;
}
```

PDO subclass
```
class DemoPDO extends PDO
{
    private $config='';                                    // Array, dictionary of all sections in .ini file
    private $dbdata='';                                    // An array, dictionary of just the [db] section

    public function __construct($iniFile) {
        $ini=$iniFile;
        $this->parseFile($ini); 
        try {
            parent::__construct($this->getDns(), $this->dbdata['dbuser'], $this->dbdata['dbpass']);
        } catch (PDOException $e) {
          print "DemoPDO::constructor() ... Base exception: " . $e->getMessage() . "<br/>";
          die();
        }
    }

    // Parse the .ini style file
    private function parseFile($ini){
       if ($ini == null) { 
          print 'DemoPDO::parseFile() ... No .ini file to parse';
          exit;
          }
       if (!$this->config = parse_ini_file($ini, TRUE)) {
          print 'DemoPDO::parseFile() ... Unable to open ' . $ini . '.';
          exit;
          }
       $this->dbdata=$this->config['db'];
    }

    // Return the database source - dns
    private function getDns(){
       $dns=$this->dbdata['dbdriver'].':host='.$this->dbdat['dbhost']. 
            ((!empty($this->dbdata['port'])) ? (';port=' . $this->dbdata['port']) : '').
            ';dbname=' . $this->dbdata['dbname'];
       return $dns;
   }

   // Extract a query from the [demo?] section in the .ini
   public function getQuery($demo, $option){
      return $this->config[$demo][$option];
   }
     
   // Run a query.  Return a PDO statement object of results.
   public function runQuery($demo, $option){
      return parent::query($this->getQuery($demo,$option));
   }
}
```

---

### Post by meastwood on 2010-11-21
Problem fixed - not really a quoting issue.  Seems to be that the PDO bindParam() and bindValue() methods have problems passing a quoted, comma separated string list. Not an issue in Python.

Solution: rewrite parts of code to build the sql statement on the fly, prepare it and then execute it i.e. not use placeholders.

---

