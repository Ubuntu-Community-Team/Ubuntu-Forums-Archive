---
title: "how to execute a transaction inside stored procedure in php multiple times"
date: 2015-08-10
forum: Programming Talk
---

### Post by shad2 on 2015-08-10
hello, i have this php 2D array:$arr[]=  array($pri,$l_pla,$my_o,$my_Ac,$my_p,$my_t);
 and would like to insert all its contents into a databse using php.
include("config.php");
for ($j = 0, $num_specials = count($arr); $j < $num_specials; $j++) {

    // $num_sub is 3: the number of elements in each sub-array
    for ($m = 0, $num_sub = count($arr[$j]); $m < $num_sub; $m++) {
        //print "Element [$j][$m] is " . $arr[$j][$m] . "\n"
    
$strat_sql="call sp_addnewdata(?,?,?,?,?,?,?)";
$insert=$mysqli->prepare($strat_sql)or die($mysqli->error);
    
           #associate variables with the input parameters
    $insert->bind_param("isssssi",$pri,$l_pla,$my_o,$my_Ac,$my_p,$my_t,$snew); 

        $pri =$arr[$j][$m];
        $l_pla=$arr[$j][$m];
            if($j>=1){$snew=1;}else{$snew=$l_planid;}

         //save record
        $my_o=$arr[$j][$m];
        $my_Ac=$arr[$j][$m];
        $my_p=$arr[$j][$m];
        $my_t=$arr[$j][$m];
           #Execute the statement
        $insert->execute(  ) or die ($insert->error);
   
$insert->close(  );
//$mysqli->close(  );
   
    }

}
It has failed so far.My stored procedure is like this:
DELIMITER $$
DROP PROCEDURE IF EXISTS sp_addnewdata $$
CREATE PROCEDURE sp_addnewstratplandetails(IN in_stratprio_id int,IN in_Planre varchar(255),in in_Outcomes varchar(255),in in_Activities varchar(255),in in_performanceIndicators varchar(255),in in_tar1 varchar(255),in in_state int)
MODIFIES SQL DATA
BEGIN
  DECLARE Result1 int;
  DECLARE pcnt1 int;
  DECLARE o_id varchar(255);DECLARE in_Outcomesrids varchar(255);
  DECLARE in_actids varchar(255);DECLARE in_pids varchar(255);
DECLARE r_id varchar(255);
DECLARE in_PLANrids varchar(255);
  DECLARE pcnt int;
 DECLARE a_id varchar(255);
 DECLARE pcntI int;
DECLARE p_id varchar(255);DECLARE in_tids varchar(255);
 DECLARE pcntt int;
 DECLARE pchk int;
 DECLARE lo_id int;
 DECLARE l_AO_id int;
DECLARE l_perfo_id int;
 DECLARE l_tar_id int;
 DECLARE t_id varchar(255);
    DECLARE in_Planid  varchar(20);
 
    DECLARE l_outcome_id  varchar(20);
    DECLARE l_Activities_id  varchar(20);
    DECLARE l_performanceIndicators_id  varchar(20);
    DECLARE l_tar  varchar(20);
  START TRANSACTION;
  SAVEPOINT savepoint_tfer;

/*check if planned result exists*/
SELECT count(*) into Result1  FROM Plantbl WHERE Planre=in_Planre and EXISTS (SELECT * FROM _strategicPlantbl WHERE      Plantbl.Planid=_strategicPlantbl.Planid and stratprio_id=in_stratprio_id);
IF Result1=0 && in_state=0 THEN
    SELECT count(*) into pcnt from Plantbl where Planid like concat(in_stratprio_id,'%');
    SET r_id=pcnt+1;
      SET in_PLANrids=concat(in_stratprio_id,'.',r_id);
            INSERT INTO Plantbl(Planid,Planre)  VALUES(in_PLANrids,in_Planre);
    
END IF;
     SELECT Planid into in_Planid FROM Plantbl WHERE Planre=in_Planre ;    

SELECT count(*) into lo_id  FROM Outcomes_tbl WHERE outcome=in_Outcomes ;
IF lo_id=0 THEN
 
    SELECT count(*) into pcnt1 from Outcomes_tbl where outcome_id like concat(in_Planid,'.','%');
    SET o_id=pcnt1+1;
      SET in_Outcomesrids=concat(in_Planid,'.',o_id);
    INSERT INTO Outcomes_tbl(outcome_id,outcome)  VALUES(in_Outcomesrids,in_Outcomes);

ELSE
    ROLLBACK TO savepoint_tfer;
    
END IF;
SELECT count(*) into l_AO_id FROM _Planresdetailstbl WHERE Activities=in_Activities;
IF l_AO_id=0 THEN
SELECT outcome_id into l_outcome_id  FROM Outcomes_tbl WHERE outcome=in_Outcomes ;
    SELECT count(*) into pcnt from _Planresdetailstbl where Activities_id  like concat(l_outcome_id,'.','%');
    SET a_id=pcnt+1;
        SET in_actids=concat(l_outcome_id,'.',a_id);
        INSERT INTO _Planresdetailstbl(Activities_id,Activities)  VALUES(in_actids,in_Activities);
ELSE
            ROLLBACK TO savepoint_tfer;
            
END IF;
SELECT count(*) into l_perfo_id  FROM _PerformanceIndicatordetailstbl WHERE performance_Indicators=in_performanceIndicators;
IF l_perfo_id=0 THEN


              SELECT count(*) into pcntI from _PerformanceIndicatordetailstbl where Pind_id  like concat(l_outcome_id,'.','%');
        SET p_id=pcntI+1;
              SET in_pids=concat(l_outcome_id,'.',p_id);
             INSERT INTO _PerformanceIndicatordetailstbl(Pind_id,performance_Indicators)  VALUES(in_pids,in_performanceIndicators);
ELSE
                ROLLBACK TO savepoint_tfer;
                  
END IF;
SELECT count(*) into l_tar_id FROM tartbl WHERE tar1=in_tar1;
IF l_tar_id=0 THEN

            SELECT count(*) into pcntt from tartbl where tar  like concat(l_outcome_id,'.','%');
            SET t_id=pcntt+1;
                SET in_tids=concat(l_outcome_id,'.',t_id);
                    INSERT INTO tartbl(tar,tar1)  VALUES(in_tids,in_tar1);
ELSE
                    ROLLBACK TO savepoint_tfer;
                      
END IF;

COMMIT;    
SELECT Activities_id into l_Activities_id FROM _Planresdetailstbl WHERE Activities=in_Activities;
SELECT Pind_id into l_performanceIndicators_id  FROM _PerformanceIndicatordetailstbl WHERE performance_Indicators=in_performanceIndicators;
SELECT tar into l_tar FROM tartbl WHERE tar1=in_tar1;

INSERT INTO _stbl(stratprio_id,Planid,outcome_id,Activities_id,Pind_id,tar )  VALUES(in_stratprio_id,in_Plan_id,l_outcome_id,l_Acti_id,l_perf_id ,l_tar_id);


END$$
DELIMITER ;
can any one tell me where iam failing??

---

