---
title: "Shell script help (sed and nslookup)"
date: 2009-05-18
forum: Programming Talk
---

### Post by kenpotf on 2009-05-18
All,

I hope someone can help me. I have the following problem. I have an ASA that I log web traffic from to an 8.10 server. I have a shell script (first one I've ever written) that greps out the address from the log and places that in a temp file. Then I run awk against that temp file to pull the ip address out only. Next, I run nslookup against all ip addresses in the temp file, and then I run sed against the result from nslookup and replace all occurrences of the ip address with the domain name that I got back from nslookup.


Below you'll see where sed is running. The result that I'm getting isn't the same as if I ran all of the steps in this script manually. The result that I'm getting (and I think it's because of the for loop), is something like this:

May 16 09:04:35 10.254.100.215 Accessed URL [B]aaaaaaaaa72-246-98-26.deploy.akamaitechnologies.com..deploy.akamaitechnologies.com..deploy.akamaitechnologies.com..deploy.akamaitechnologies.com..deploy.akamaitech
nologies.com..deploy.akamaitechnologies.com..deploy.akamaitechnologies.com..deploy.akamaitechnologies.com..deploy.akamaitechnologies.com.:[/B]/adx/images/ADS/19/99/ad.199919/global_728x90a.jpg

I should only see the domain name one time, but it's doing this for multiple and I can't figure out why. I know that one thing that happens is sometimes nslookup returns a blank result, and I think this could be some of the problem, but I don't know how to error check that, and I'm not a developer by ANY stretch of the imagination. ;-)


Here's the script:

#!/bin/sh

# Remove old files

rm -rf /var/log/results
rm -rf /var/log/resultsfiltered
rm -rf /var/log/reportFinished

# Notify the user that the query is running - It can take a while
echo "\n\n\nRunning report...please wait...\n"

# Run the query and write the results to a file "results"

grep "ASA-5-304001" cisco.log | grep $1 | awk  '{print $1,$2,$3,$6,$7,$8,$9,$10}' > results

# Pull all ip addresses out of the results file, and then write them to resultsfiltered

awk -F" " '{ print $7 }' testResults | awk -F: '{ print $1 }' > resultsfiltered

fileAddress=`cat ./resultsfiltered`

touch addressTMP

# Open resultsfiltered and run nslookup on each ip address in it

for a in $fileAddress; do
        echo "Running nslookup on $a"
        domain=`nslookup $a | grep "name =" | awk '{ print $4 }'`
        echo "Getting domain name...."
        sed -i "s/$a/$domain/g" results      # Run sed against the results file and replace the ip address with the result
        echo "I put $domain in place of $a"
        sleep 5
done                                            # from nslookup

# Inform the user that the report is being ran
echo "\n\n\n\n\nCopying final results to report...\n\n\n\n\n"

echo "We're done with the loop."

# copy the results file that sed modified to reportFinished

cp /var/log/results /var/log/reportFinished

# Insert a line at the top of the report that tells what IP address the report was ran for.
#sed "1i\Report for $1 \n\n\n\n" reportFinished

# Clean up
#rm -rf addressTMP


Thank you!!!

John

---

### Post by DaithiF on 2009-08-23
Hi,
to read a file line by line you should use this approach:
```
while read a
do
  # do stuff with $a
done < resultsfiltered

```

rather than the one below:
```
fileAddress=`cat ./resultsfiltered`
for a in $fileAddress; do
        echo "Running nslookup on $a"
        ...
done                                            # from nslookup
```

---

