---
title: "how-to-make-a-mysql-transaction- ececute multiple times in php"
date: 2015-07-09
forum: Programming Talk
---

### Post by shad2 on 2015-07-09
ihave three tables.I need to populate them with data.

    create table heading(head varchar(10),title varchar(100));
    create table subheading(shead varchar(10),stitle varchar(100));
    create table subheading2(s2head varchar(10),s2title varchar(100));

the contents in subheading and subheading2 are present if a  head present in heading 
such that
i have this mapping:

         heading         subhead1          subhead2
H1                          VAL1A                      VAL2A
                                                                                                               VAL2B
                                           VAL1B                       VAL2C

how can i use a transaction to insert the records.Currently my transaction is as below but inserts only :

    heading          subhead1                  subhead2
    H1                              VAL1A                            VAL2A

transaction:

    CREATE PROCEDURE sp_addnewdetails(IN in_stratp int,IN in_haeding     varchar(255),in in_subhead1 varchar(255),in in_subhead2 varchar(255))
    MODIFIES SQL DATA
    BEGIN
    DECLARE Result1 int;
    DECLARE pcnt1 int;
    DECLARE o_id varchar(255);DECLARE in_Out_csrids varchar(255);
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
    DECLARE in_i_Plalid_id  varchar(20);
  
    DECLARE l_Out_c_id  varchar(20);
    DECLARE l_Actis_id  varchar(20);
    DECLARE l_perors_id  varchar(20);
    DECLARE l_tart_id  varchar(20);
    START TRANSACTION;
    SAVEPOINT savepoint_tfer;

    /*check if heading exists*/
    SELECT count(*) into Result1  FROM i_Plal WHERE i_Plalid=in_heading;
    IF Result1=0  THEN
    SELECT count(*) into pcnt from heading ;
    SET r_id=pcnt+1;
      SET in_PLANrids=concat(in_stratp,'.',r_id);
            INSERT INTO heading(head,title)  VALUES(in_PLANrids,in_heading);
    
    END IF;

    SELECT count(*) into lo_id  FROM Outc WHERE Out_c=in_Out_cs ;
    IF lo_id=0 THEN
 
    SELECT count(*) into pcnt1 from Outc where Out_c_id like concat(in_i_Plalid_id,'.','%');
    SET o_id=pcnt1+1;
      SET in_Out_csrids=concat(in_i_Plalid_id,'.',o_id);
    INSERT INTO Outc(Out_c_id,Out_c)  VALUES(in_Out_csrids,in_Out_cs);

    ELSE
    ROLLBACK TO savepoint_tfer;
    SELECT CONCAT('Saving record aborted! Out_c "',in_Out_cs,'" already exists');
    END IF;
    SELECT count(*) into l_AO_id FROM _i_Plalidsdetailstbl WHERE Activities=in_Aes; 
    IF l_AO_id=0 THEN
    SELECT Out_c_id into l_Out_c_id  FROM Outc WHERE Out_c=in_Out_cs ;
    SELECT count(*) into pcnt from _i_Plalidsdetailstbl where Acs_id  like concat(l_Out_c_id,'.','%');
    SET a_id=pcnt+1;
        SET in_actids=concat(l_Out_c_id,'.',a_id);
        INSERT INTO _i_Plalidsdetailstbl(Acs_id,Activities)  VALUES(in_actids,in_Aes);
    ELSE
            ROLLBACK TO savepoint_tfer;
            SELECT CONCAT('Saving record aborted  Acity  "',in_Aes,'" already Exists! ');
    END IF;
    SELECT count(*) into l_perfo_id  FROM _Pelstbl WHERE pere_Indiors=in_pericators;
    IF l_perfo_id=0 THEN


              SELECT count(*) into pcntI from _Pelstbl where Pi_id  like concat(l_Out_c_id,'.','%');
        SET p_id=pcntI+1;
              SET in_pids=concat(l_Out_c_id,'.',p_id);
             INSERT INTO _Pelstbl(Pi_id,pere_Indiors)  VALUES(in_pids,in_pericators);
    ELSE
                ROLLBACK TO savepoint_tfer;
                    SELECT  CONCAT('Saving record aborted perfodicator "',in_pericators,'" already Exists! ');
    END IF;
    SELECT count(*) into l_tar_id FROM _Tartbl WHERE target=in_taet;
    IF l_tar_id=0 THEN

            SELECT count(*) into pcntt from _Tartbl where Tart_id  like concat(l_Out_c_id,'.','%');
            SET t_id=pcntt+1;
                SET in_tids=concat(l_Out_c_id,'.',t_id);
                    INSERT INTO _Tartbl(Tart_id,target)  VALUES(in_tids,in_taet);
    ELSE
                    ROLLBACK TO savepoint_tfer;
                        SELECT CONCAT('Saving record aborted tt "',in_taet,'" already Exists! ');
    END IF;

    
    SELECT Acs_id into l_Actis_id FROM _i_Plalidsdetailstbl WHERE Activities=in_Aes; 
    SELECT Pi_id into l_perors_id  FROM _Pelstbl WHERE pere_Indiors=in_pericators;
    SELECT Tart_id into l_tart_id FROM _Tartbl WHERE target=in_taet;

    INSERT INTO _stratbl(stratprio_id,i_Plalid_id,Out_c_id,Acs_id,Pi_id,Tart_id )  VALUES(in_stratp,in_i_Plalid_id,l_Out_c_id,l_Actis_id,l_perors_id ,l_tart_id);
    SELECT 'success ';

    COMMIT;
    END

iam using this php:

    include("config.php");

    $strat_sql="call sp_addnewstratplandetails(?,?,?,?,?,?,?)";
    $insert_strat_stmt=$mysqli->prepare($strat_sql)or die($mysqli->error);
           #associate variables with the input parameters
           $insert_strat_stmt->bind_param("isssssi",$my_prioid,$my_planid,$my_outcome_id,$my_Activities_id,$my_performanceIndicator_id,$my_target_id,$snew); #i=integer

    //aggregate the records to save
    for($col=0;$col<count($outcome);$col++){
        $my_prioid =$_POST['strat_priorities'];
        $my_planid=stripslashes($plan);

        $pos=$col;
        $out=$oume[$col];
            $act=$aity[$col];
        $ind=$inator[$col];
            $tar=$taet[$col];
    

         //save record
        $my_outcome_id=stripslashes($out);
        $my_Activities_id=stripslashes($act);
        $my_performanceIndicator_id=stripslashes($ind);
        $my_target_id=stripslashes($tar);
           #Execute the statement
        $insert_strat_stmt->execute(  ) or die ($insert_strat_stmt->error);
        $insert_strat_stmt->bind_result($Entryerr);
        while ($insert_strat_stmt->fetch(  )) {
             $error12=$Entryerr;//trap 1062error from here into warnecho $Rnotes;//= $row->warning ;
            if(substr($error12,0, 4)=="Tran"){$errorb[]=$error12;}//else{$suc=$error12;}//elseif(substr($error12,0, 4)=="Warn"){$planerr=$error12;}
        }    
    
    }//end for

    $insert_strat_stmt->close(  );
    $mysqli->close(  );

---

