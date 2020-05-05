# Install-Splunk-UF-on-Databricks-Cluster

* Import ***Install Splunk UF on Databricks Cluster.ipynb*** notebook
  * url: `https://raw.githubusercontent.com/rzzldzzl/Install-Splunk-UF-on-Databricks-Cluster/master/Install%20Splunk%20UF%20on%20Databricks%20Cluster.ipynb`
* Set Variables (These can also be set in each Cluster's Environmnet Variables Config)
  * ufDlUrl=`"https://download.splunk.com/products/universalforwarder/releases/8.0.2.1/linux/splunkforwarder-8.0.2.1-f002026bad55-Linux-x86_64.tgz"`
  * ufDlDir=`"/dbfs/splunkUF"`
  * ufInstallDir=`"/local_disk0"`
  * ARGETURI=`"<FQDN of Splunk Deployment Server>:8089"`
* Execute ***Install Splunk UF on Databricks Cluster*** notebook to write `splunkUF-init.sh` init script.
* Configure Splunk UF configs on Deployment Server - see examples
  * Indexing Tier
    * splunk_example_configs/idx/etc/apps/dbr/local/indexes.conf
      * *create DBR specifc index*
    * splunk_example_configs/idx/etc/apps/dbr/local/props.conf
      * *temporarily disable TRUNCATE*
    * splunk_example_configs/idx/etc/apps/dbr/local/inputs.conf
      * *configure inputs*
  * Deployment Server
    * splunk_example_configs/ds/etc/deployment-apps/dbr/default/outputs.conf
      * *configure outputs*
    * splunk_example_configs/ds/etc/deployment-apps/dbr/default/inputs.conf
      * *configure inputs*
    * splunk_example_configs/ds/etc/apps/dbr/local/serverclass.conf
      * *configure serverclass*
* Configure Databricks cluster to run init script `dbfs:/splunkUF/splunkUF-init.sh`
