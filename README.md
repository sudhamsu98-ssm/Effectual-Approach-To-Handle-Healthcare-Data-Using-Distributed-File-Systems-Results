# Effectual-Approach-To-Handle-Healthcare-Data-Using-Distributed-File-Systems-Results
Softwares to be installed
Install  Hadoop 3.2.1 Multi-Node Cluster on Ubuntu 18.04 https://medium.com/@jootorres_11979/how-to-set-up-a-hadoop-3-2-1-multi-node-cluster-on-ubuntu-18-04-2-nodes-567ca44a3b12
Install Mysql :
mysql -u root -p   this only works if u install the mysql correctly

Elasticsearch installation:

How To Install Elasticsearch, Logstash and Kibana on Ubuntu 18.04

Requirment
    login: user with root privileges
    OS: Ubuntu 18.04
    RAM: 4GB
    CPU: 2
    Java: Oracle JDK 8 version

The same instructions apply for Ubuntu 17.04/16.04, Linux Mint, Debian, Kubuntu and Elementary OS

Update/upgrade
1. sudo apt update
2. sudo apt-get upgrade -y
-------------------------------------------------------
Install dependencies and java 8
1. sudo add-apt-repository ppa:webupd8team/java
2. sudo apt-get update OR sudo apt update
3. sudo apt install openjdk-8-jdk

Verify the Java
1. java -version


1. ELASTICSEARCH

ELASTICSEARCH

Install and configure Elasticsearch
1. cd /tmp
2. wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.5.2-amd64.deb
3. sudo dpkg -i elasticsearch-7.5.2-amd64.deb

Elasticsearch configuration file
1. sudo nano /etc/elasticsearch/elasticsearch.yml
network.host to [local, eth0] 
nano /etc/init.d/elasticsearch

Locate the line:
# network.host: localhost

start and enable the service 
1. sudo systemctl enable elasticsearch.service
2. sudo systemctl start elasticsearch.service
       sudo systemctl status elasticsearch.service
OR
/etc/init.d/elasticsearch start
3. /etc/init.d/elasticsearch status


Verify Elasticsearch
1. curl -X GET "localhost:9200/"

open web browser
1. http://server_ip:9200/ or http://localhost:9200/

#docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:5.0.0(not required)


2. KIBANA

Now, Install and configure Kibana
1. cd /tmp
2. wget https://artifacts.elastic.co/downloads/kibana/kibana-7.5.2-amd64.deb
3. sudo dpkg -i kibana-7.5.2-amd64.deb

Configuration file Kibana
1. sudo nano /etc/kibana/kibana.yml

    Locate the following lines:
#server.host: "localhost"
#elasticsearch.url: "http://localhost:9200"
to
Change those lines to:
server.host: "SERVER_IP"
elasticsearch.hosts: "http://SERVER_IP:9200"

1. sudo sysctl -w vm.max_map_count=262144

start and enable the service
1. sudo systemctl enable kibana.service
2. sudo systemctl start kibana.service
3. sudo systemctl status kibana.service

open web browser
1. http://server_ip:5601/ or ip_address:560


3.LOGSTASH

Now, Install and configure Logstash
1. cd /tmp
2. wget https://artifacts.elastic.co/downloads/logstash/logstash-7.5.2.deb
3. sudo dpkg -i logstash-7.5.2.deb

Configuration file logstash
1. sudo nano /etc/logstash/logstash.yml

Locate the line:
# http.host: "127.0.0.1"

start and enable the service
1. sudo systemctl enable logstash.service
2. sudo systemctl start logstash.service
3. sudo systemctl status logstash.service

start-commands:
1.  sudo systemctl start kibana.service
2.   sudo systemctl start logstash.service
3.    sudo systemctl start  elasticsearch.service

stop-commands:
1. sudo systemctl stop kibana.service
2.  sudo systemctl stop logstash.service
3. sudo systemctl stop  elasticsearch.service

 Spark Installation
 sudo apt-get update  

---- Install  java and set up path for java -------
sudo apt-get install openjdk-8-jdk 

export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64 >> ~/.bashrc
export JRE_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre ~/.bashrc
source ~/.bashrc


---Download Spark and Configure path and Start Spark master and Worker ------

wget https://mirrors.estointernet.in/apache/spark/spark-3.0.1/spark-3.0.1-bin-hadoop2.7.tgz

tar -xvzf spark-*

mv spark-3.0.1-bin-hadoop2.7/ /opt/spark

echo "export SPARK_HOME=/opt/spark" >> ~/.bashrc

echo "export PATH=$PATH:/opt/spark/bin:/opt/spark/sbin" >> ~/.bashrc

echo "export PYSPARK_PYTHON=/usr/bin/python3" >> ~/.bashrc

source ~/.bashrc

start-master.sh 

start-slave.sh spark://<ip address of System/Server>:7077

---check spark-shell and pyspark working ------

spark-shell  ---> should open scala shell prompt

pyspark ---- should start python prompt 


----install pip and jupyter notebook and configuration -----

curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
sudo python3 get-pip.py
sudo pip3 install jupyter
sudo pip3 install pyspark


echo "export PYSPARK_DRIVER_PYTHON="jupyter"" >> ~/.bashrc
echo "export PYSPARK_DRIVER_PYTHON_OPTS="notebook"" >> ~/.bashrc
echo "export PYSPARK_PYTHON=python3" >> ~/.bashrc

source ~/.bashrc

---start jupyter notebook and test pyspark----

jupyter notebook 

SQOOP INSTALLATION :


1.  We can download the latest version of Sqoop from the following https://mirrors.estointernet.in/apache/sqoop/

* The following commands are used to extract the Sqoop tar ball and move it to “/usr/lib/sqoop” directory.

tar -xvf  sqoop-1.4.7.bin__hadoop-2.6.0.tar.gz

sudo mv  sqoop-1.4.7.bin__hadoop-2.6.0 /usr/lib/sqoop


2. Configuring bashrc

#Sqoop
export SQOOP_HOME=/usr/lib/sqoop
export PATH=$PATH:$SQOOP_HOME/bin
3. Download and Configure mssql-connector-java

https://docs.microsoft.com/en-us/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15

tar -zxf   sqljdbc_9.2.1.0_enu.tar.gz
 
sudo mv  sqljdbc_9.2.1.0_enu.tar.gz  usr/lib/sqoop/lib


4.  Verifying Sqoop
 
cd $SQOOP_HOME/bin

 sqoop-version
Warning: /usr/lib/sqoop/../hbase does not exist! HBase imports will fail.
Please set $HBASE_HOME to the root of your HBase installation.
Warning: /usr/lib/sqoop/../hcatalog does not exist! HCatalog jobs will fail.
Please set $HCAT_HOME to the root of your HCatalog installation.
Warning: /usr/lib/sqoop/../accumulo does not exist! Accumulo imports will fail.
Please set $ACCUMULO_HOME to the root of your Accumulo installation.
Warning: /usr/lib/sqoop/../zookeeper does not exist! Accumulo imports will fail.
Please set $ZOOKEEPER_HOME to the root of your Zookeeper installation.
/opt/hadoop//libexec/hadoop-functions.sh: line 2366: HADOOP_ORG.APACHE.SQOOP.SQOOP_USER: bad substitution
/opt/hadoop//libexec/hadoop-functions.sh: line 2461: HADOOP_ORG.APACHE.SQOOP.SQOOP_OPTS: bad substitution
2021-03-12 11:25:14,624 INFO sqoop.Sqoop: Running Sqoop version: 1.4.7
Sqoop 1.4.7
git commit id 2328971411f57f0cb683dfb79d19d4d19d185dd8
Compiled by maugli on Thu Dec 21 15:59:58 STD 2017
 

refer  https://www.tutorialspoint.com/sqoop/index.htm for installation

 sqoop import --connect jdbc:mysql://localhost:3306/ myclassdb --username root --password sudhamsu  --table  WPW_1  --split-by mamana_3012   --m 1

   ---command to export data

 sqoop import \
 --connect jdbc:mysql://localhost:3306/myclassdb \
--username root \
 --password sudhamsu \
- --password sudhamsu \
--table  WPW_1  \
--split-by mamana_3012 \
--m 1
sqoop import \
 --connect jdbc:mysql://sandbox-hdp.hortonworks.com/sqoop \
 --username root \
 --password hadoop \
 --table HR \
 --target-dir /sqoop/hr \
 --driver com.mysql.jdbc.Driver \
 --split-by mamana_3012










