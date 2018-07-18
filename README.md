## User Count ##
  
To compile the project:

1) Open in Eclisle
2) set HBASE_HOME  class variable to hbase install dir

### Setup hbase tables ###  

open hbase shell
``` $ hbase shell 
        create 'access_logs', 'details'
	  	create 'summary_user', {NAME=>'details', VERSIONS=>1}
```
		
'access_logs' is the 'raw' logs.  The key is userID+counter  (int + int)
'summary_user' is to compute summary.  key is 'userID' (int)

### Running map reduce ###  

* Run 'FreqCounter1' directly from Eclipse, as a Java application

### Run on cluster / command line ###
* make a jar ```jar cf freqCounter.jar -C classes ```

* ``` hadoop jar freqCounter.jar hbase_mapred1.FreqCounter1 ```

* check progress at task tracker : http://localhost:50070

