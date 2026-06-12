---
title: "Problem in accessing the native code (c++) in PHP using Swig"
date: 2012-09-14
forum: Programming Talk
---

### Post by Antrikssh on 2012-09-14
Hi,

I have created EmployeeNative class in Native (C++) and created EmployeeSwig class using SWIG. EmployeeSwig class is just wrapper class to access EmployeeNative class functionalities.

_**Native Class Definition:**_
class EmployeeNative {
    private:
        int iEmpCode;

    public:
        EmployeeNative ();
        ~EmployeeNative ();
        int SetEmpCode (int iSetCode);
        int GetEmpCode ();
};

_**SWIG Class definition:**_
class EmployeeSwig {
    private:
        EmployeeNative *pEmpNative ;

    public:
        EmployeeSwig ();
        ~EmployeeSwig ();
        int SetEmpCode (int iSetCode);
        int GetEmpCode ();
};


I have created two PHP scripts Server.php and Client.php. 

**_Server.php:_**
<?php
    session_start();
    include("EmployeeSwig.php");

    $EmpSwig = new EmployeeSwig();
    $iRetVal = 0;
    $iSetVal = 50;

    $iRetVal = $EmpSwig->SetEmpCode($iSetVal);
    $iRetVal = $EmpSwig->GetEmpCode();
    
    $_SESSION['EmpSwigObj'] = $EmpSwig;
    session_write_close();

    var_dump($_SESSION['EmpSwigObj']);

    $iLoopCounter = 0;
    while ($iLoopCounter < 20) {
        $iLoopCounter++;
        sleep(1);
    }
?>

_**Client.php:**_
<?php
    session_id('h949k2vgorl88k21illifoteg3');  // Same Session Id; Retrieved from server script.
    include("EmployeeSwig.php");
    session_start();

    $EmpSwig = $_SESSION['EmpSwigObj'];
    
    var_dump($_SESSION['EmpSwigObj']);

    $iRetVal = $EmpSwig->GetEmpCode();    
?>

In server.php script, I am storing the object of EmployeeSwig class in session variables.
In Client.php script, I am retreiving the object of EmployeeSwig class from session Variables.

Now In Client.php script, I am calling the member function of EmployeeSwig object. But it is giving me error as "PHP Fatal error: Type error in argument 1 of EmployeeSwig_GetEmpCode. Expected SWIGTYPE_p_EmployeeSwig 

When I tried to debug furthur using var_dump, I found following observation:
_**OutPut of var_dump from Server.php script:**_
object(EmployeeSwig)#1 (2) {
  ["_cPtr"]=>
  resource(5) of type (_p_EmployeeSwig)
  ["_pData": protected]=>
  array(0) {
  }
}

**_Output of var_dump from Client.php script:_**
object(EmployeeSwig)#1 (2) {
  ["_cPtr"]=>
  int(0)
  ["_pData": protected]=>
  array(0) {
  }
}

**_Strange observation: _**
In Server.php script,Array index ["_cPtr"]  is pointing as ["_cPtr"]=>resource(5) of type (_p_EmployeeSwig)
In Client.php script, Array Index ["_cPtr"]  is pointing as ["_cPtr"]=>int(0).

Why it is showing different values for Array Index ["_cPtr"] in Server and Client php script and how to address this problem?

Thanks and Regards,

Antrikssh...

---

