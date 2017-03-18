# MySQL Connector/J

MySQL provides connectivity for client applications developed in the Java programming language with MySQL Connector/J, a driver that implements the [Java Database Connectivity (JDBC) API](http://www.oracle.com/technetwork/java/javase/jdbc/).

MySQL Connector/J 5.1 is a JDBC Type 4 driver that is compatible with the [JDBC 3.0](http://docs.oracle.com/javase/1.5.0/docs/guide/jdbc/), [JDBC 4.0](http://docs.oracle.com/javase/6/docs/technotes/guides/jdbc/), [JDBC 4.1](http://docs.oracle.com/javase/7/docs/technotes/guides/jdbc/) and [JDBC 4.2](http://docs.oracle.com/javase/8/docs/technotes/guides/jdbc/) specifications. The Type 4 designation means that the driver is a pure Java implementation of the MySQL protocol and does not rely on the MySQL client libraries.

For detailed information please visit the official [MySQL Connector/J documentation](http://dev.mysql.com/doc/connector-j/en/).

## Licensing

Please refer to files README and COPYING, available in this repository, and [Legal Notices in documentation](http://dev.mysql.com/doc/connector-j/en/preface.html) for further details. 

## Download & Install

MySQL Connector/J can be installed from pre-compiled packages that can be downloaded from the [MySQL downloads page](http://dev.mysql.com/downloads/connector/j/). Installing Connector/J only requires extracting the corresponding Jar file from the downloaded bundle and place it somewhere in the application's CLASSPATH.

Alternatively you can setup [Maven's dependency management](http://search.maven.org/#search|ga|1|g%3A%22mysql%22%20AND%20a%3A%22mysql-connector-java%22) directly in your project and let it download it for you.

### Building from sources

This driver can also be complied and installed from the sources available in this repository. Please refer to the documentation for [detailed instructions](http://dev.mysql.com/doc/connector-j/en/connector-j-installing-source.html) on how to do it.

### GitHub Repository

This repository contains the MySQL Connector/J source code as per latest released version. You should expect to see the same contents here and within the latest released Connector/J package, except for the pre-compiled Jar.

## Additional resources

- [MySQL Connector/JDBC and Java forum](http://forums.mysql.com/list.php?39)
- [MySQL and Java Mailing Lists](http://lists.mysql.com/java)
- [InsideMySQL Connectors Blog](http://insidemysql.com/category/mysql-development/connectors/)
- [MySQL Connectors Java Blog](https://blogs.oracle.com/mysqlconnectors-java)
- [MySQL Bugs database](http://bugs.mysql.com/)
- For more information about this and other MySQL products, please visit [MySQL Contact & Questions](http://www.mysql.com/about/contact/).



## how to build

* 安装ant。
* 配置两个jdk，5和8。并修改build.xml配置，如下：
```
    <property name="com.mysql.jdbc.jdk5" value="/usr/java/jdk1.5.0_15" />
    <property name="com.mysql.jdbc.jdk8" value="/home/vagrant/java/jdk1.8.0_73" />

```

* 上传hibernate4必须包到src/lib/hibernate4/下。
* 上传junit包到src/lib/下。
* 可能会出现如下报错，这个是jdk的bug，用的jdk版本是jdk-1_5_0_15，需要使用jdk1.5.0_22。
```
compile-testsuite:
     [echo] Compiling MySQL Connector/J testsuite with '/usr/java/jdk1.5.0_15' to './build/mysql-connector-java-5.1.40-SNAPSHOT'
    [javac] Compiling 62 source files to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT
    [javac] An exception has occurred in the compiler (1.5.0_15). Please file a bug at the Java Developer Connection (http://java.sun.com/webapps/bugreport)  after checking the Bug Parade for duplicates. Include your program and the following diagnostic in your report.  Thank you.
    [javac] java.lang.AssertionError: {rawtypes}
    [javac] 	at com.sun.tools.javac.tree.TreeMaker$AnnotationBuilder.visitArray(TreeMaker.java:634)
    [javac] 	at com.sun.tools.javac.code.Attribute$Array.accept(Attribute.java:124)
    [javac] 	at com.sun.tools.javac.tree.TreeMaker$AnnotationBuilder.translate(TreeMaker.java:637)
    [javac] 	at com.sun.tools.javac.tree.TreeMaker$AnnotationBuilder.visitCompoundInternal(TreeMaker.java:628)
    [javac] 	at com.sun.tools.javac.tree.TreeMaker$AnnotationBuilder.translate(TreeMaker.java:641)
    [javac] 	at com.sun.tools.javac.tree.TreeMaker.Annotation(TreeMaker.java:649)
    [javac] 	at com.sun.tools.javac.tree.TreeMaker.Annotations(TreeMaker.java:570)
    [javac] 	at com.sun.tools.javac.tree.TreeMaker.VarDef(TreeMaker.java:554)
    [javac] 	at com.sun.tools.javac.comp.Lower.visitIterableForeachLoop(Lower.java:2892)
    [javac] 	at com.sun.tools.javac.comp.Lower.visitForeachLoop(Lower.java:2755)
    [javac] 	at com.sun.tools.javac.tree.Tree$ForeachLoop.accept(Tree.java:597)
    [javac] 	at com.sun.tools.javac.comp.Lower.translate(Lower.java:1881)
    [javac] 	at com.sun.tools.javac.tree.TreeTranslator.translate(TreeTranslator.java:54)
    [javac] 	at com.sun.tools.javac.tree.TreeTranslator.visitBlock(TreeTranslator.java:145)
    [javac] 	at com.sun.tools.javac.comp.Lower.visitBlock(Lower.java:2927)

```

```
    <property name="com.mysql.jdbc.jdk5" value="/usr/java/jdk1.5.0_22" />
    <property name="com.mysql.jdbc.jdk8" value="/home/vagrant/java/jdk1.8.0_73" />

```

* 执行ant成功编译。
```
[root@hb-localhost m2o-mysql-connector]# ant 
Buildfile: /home/vagrant/m2o-proxy/m2o-mysql-connector/build.xml

-jdk5-check:

-jdk8-check:

-jre6-rtjar-check:

-compiler-check:

clean:
   [delete] Deleting directory /home/vagrant/m2o-proxy/m2o-mysql-connector/build

-init-copy-common:
    [mkdir] Created dir: /home/vagrant/m2o-proxy/m2o-mysql-connector/build
     [copy] Copying 364 files to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT
     [copy] Copied 52 empty directories to 1 empty directory under /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT
     [copy] Copying 13 files to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT

-replace-headers-commercial:

-init-copy:

-extra-libs-check:

-init-filter-license:

-init-no-crypto:

init:

-clean-output:

-compile-driver-jdbc3:
     [echo] Compiling MySQL Connector/J JDBC 3 implementation with '/home/vagrant/java/jdk1.5.0_22' to './build/mysql-connector-java-5.1.40-SNAPSHOT'
    [javac] Compiling 218 source files to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT

-compile-driver-jdbc4:
     [echo] Compiling MySQL Connector/J JDBC 4+ implementation with '/home/vagrant/java/jdk1.8.0_73' to './build/mysql-connector-java-5.1.40-SNAPSHOT'
    [javac] Compiling 41 source files to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT
    [javac] warning: [options] bootstrap class path not set in conjunction with -source 1.6
    [javac] 1 warning
    [javac] Compiling 8 source files to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT

compile-driver:

compile-testsuite:
     [echo] Compiling MySQL Connector/J testsuite with '/home/vagrant/java/jdk1.5.0_22' to './build/mysql-connector-java-5.1.40-SNAPSHOT'
    [javac] Compiling 62 source files to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT
    [javac] Compiling 5 source files to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT
    [javac] warning: [options] bootstrap class path not set in conjunction with -source 1.6
    [javac] 1 warning
    [javac] Compiling 4 source files to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT

-compile-integration-c3p0:
     [echo] Compiling MySQL Connector/J-c3p0 integration with '/home/vagrant/java/jdk1.5.0_22' to './build/mysql-connector-java-5.1.40-SNAPSHOT'
    [javac] Compiling 1 source file to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT

-compile-integration-jboss:
     [echo] Compiling MySQL Connector/J-jboss integration with '/home/vagrant/java/jdk1.5.0_22' to './build/mysql-connector-java-5.1.40-SNAPSHOT'
    [javac] Compiling 1 source file to /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT

-compile-integration-log4j:

compile-integration:

compile:

dist:
    [mkdir] Created dir: /home/vagrant/m2o-proxy/m2o-mysql-connector/build/META-INF
    [mkdir] Created dir: /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT/META-INF/services
      [jar] Building jar: /home/vagrant/m2o-proxy/m2o-mysql-connector/build/mysql-connector-java-5.1.40-SNAPSHOT/mysql-connector-java-5.1.40-SNAPSHOT-bin.jar

BUILD SUCCESSFUL
Total time: 52 seconds

```
