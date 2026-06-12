---
title: "Bash Scripting - Dangerous Code seeker"
date: 2011-10-18
forum: Programming Talk
---

### Post by skraps on 2011-10-18
I'm working on a script to hunt down dangerous code or good spots to start when looking for injections. I'm trying to consolidate space by turning the mainly used loops in to seperate functions. But I'm having problems passing a array back with return. I understand now that a array cannot be passed back with return only integer values. Is there a way to create dynamicly named variables based on the arguments passed ie: $1 = "exe" , to store a value to ${1}numresults
[*] so I can access the information outside the function but it doesnt get over wrote when the function is used again?
```

method=("_GET\[" "_POST\[" "_REQUEST\[")
sql=("SELECT" "UPDATE" "INSERT")
wpdb=("get_results" "query" "get_var" "get_row")
file=("get_file_contents(" "fopen(")
exe=("exec(" "system(" "passthru(" "pcntl_exec(" "eval(")

tmpdir="${PWD}/tmp.fgs"

mkdir ${tmpdir} 2>/dev/null
if [ $? > '0' ];then
        rm -fr ${tmpdir}
        mkdir ${tmpdir} 2>/dev/null
fi

if [ -z "$1" ]; then
        path="./*"
else
        path=$1
fi

function findstr(){
        c2='0'
        declare -a argAry1=("${!2}")

        for a in "${argAry1[@]}";do
                echo "   [ Searching for $a ]"
                grep -n $a $path >> ${tmpdir}/gsf${1}.tmp

                if [ $? = 1 ];then
                        echo "      !! - No Results - !!"
                else
                        numresults[$c2]=`cat ${tmpdir}/gsf${1}.tmp |grep $a| wc -l`
                        echo "      !! - ${numresults[$c2]} - !!"
                fi
                c2=$(($c2+1))
        done


        return $numresults
}

function getpost(){
count='0'
for a in "${method[@]}";do
        echo "         [ Searching for $a ]"
        grep -n $a ${tmpdir}/gsf${1}.tmp >> ${tmpdir}/gsf${1}${a}.tmp

        if [ $? = 1 ];then
                echo "            !! - No Results - !!"
        else
                numresults[$count]=`cat ${tmpdir}/gsf${1}${a}.tmp | wc -l`
                echo "            !! - ${numresults[$count]} - !!"
        fi
        count=$(($count+1))
done
return $numresults
}
echo "[=====================-------------------=========================]"
echo "[ Script to hunt down the good stuff for finding web app exploits ]"
echo "[=====================-------------------=========================]"
echo "[ By skraps ]=====================================================]"
echo "[ jackie.craig.sparks@{live,gmail}.com ]==========================]"
echo "[ communicationslibrary.info phonesnake.com ]=====================]"
echo "[=================================================================]"
echo -ne "\n"
echo "[ Searching ${PWD} ]"

echo "[ Searching for Possible Command Injections Spots ]"
exenumresults= findstr exe exe[@]
echo ${exenumresults}
if [ -n "${exenumresults
[*]}" ];then
       exegpnumresults= getpost exe
fi
exit
echo "[ Searching for GET and POST ]"

for a in "${method[@]}";do
        echo "  [ Searching for $a ]"
        grep -n $a ${path} >> ${tmpdir}/gsfgetpost${a}.tmp

        if [ $? = 1 ];then
                echo "     !! - No Results - !!"
        else
                getpostnumresults=`cat ${tmpdir}/gsfgetpost${a}.tmp | wc -l`
                echo "     !! - $getpostnumresults - !!"
        fi
done

c2='0'
echo "[ Searching for Possible SQL Injections spots ]"
for a in "${sql[@]}";do
echo "   [ Searching for $a ]"
        grep -ni $a $path >> ${tmpdir}/gsfsql.tmp

        if [ $? = 1 ];then
                echo "      !! - No Results - !!"
        else
                sqlnumresults[$c2]=`cat ${tmpdir}/gsfsql.tmp | wc -l`
                echo "      !! - ${sqlnumresults[$c2]} - !!"
        fi
        c2=$(($c2+1))
done

if [ -n "${sqlnumresults
[*]}" ];then
       sqlnumresults= getpost sql
fi

c2='0'
echo "[ Searching for Possible File exec and Recursion ]"
for a in "${file[@]}";do
        echo "   [ Searching for $a ]"
        grep -n $a $path >> ${tmpdir}/gsffile.tmp

        if [ $? = 1 ];then
                echo "      !! - No Results - !!"
        else
                filenumresults[$c2]=`cat ${tmpdir}/gsffile.tmp | wc -l`
                echo "      !! - ${filenumresults[$c2]} - !!"
        fi
        c2=$(($c2+1))
done

if [ -n "${filenumresults
[*]}" ];then
       filenumresults= getpost file
fi


echo "[ Wordpress sql queries without prepare ]"
for i in "${wpdb[@]}";do
        grep -n "wpdb->${i}(" $path >> ${tmpdir}/gsfwpdb.tmp
done

grep -n "wpdb->prepare(" ${tmpdir}/gsfwpdb.tmp > ${tmpdir}/gsfwpdbpre.tmp

if [ $? = 1 ]; then
        echo "   !! - No Results - !!"
else
        preparenumresults=`cat ${tmpdir}/gsfwpdbpre.tmp | wc -l`
        echo "   !! - $preparenumresults - !!"
fi

cat ${tmpdir}/* > ${HOME}/fgs.output
echo "Output of results saved: ${HOME}/fgs.output"

#remove temp files
rm -fr ${tmpdir}


echo "Press RETURN to view output or type \"q\" to quit"
read res

if [ -e $res ];then
        cat ${HOME}/fgs.output | sort -u | less
fi



```

---

