Kitchensink on OpenShift
=========================

This is the kitchensink JBoss quickstart app.  You can find more info @ http://www.jboss.org/jdf/quickstarts/jboss-as-quickstart/guide/KitchensinkQuickstart/

Running on OpenShift
--------------------

Create an account at https://www.openshift.com

Create a jbossas-7 application

    rhc app create kitchensink jbossas-7 --from-code git://github.com/openshift/kitchensink-example.git

That's it, you can now checkout your application at:

    http://kitchensink-$namespace.rhcloud.com

mysql-5.5 as a backend
-----------------------
this quickstart uses mysql as the backend

To do this, add PostgreSQL cartridge to your application:

    rhc cartridge add mysql-5.5 -a kitchensink

Edit `src/main/resources/META-INF/persistence.xml` so that the data
source points to `java:jboss/datasources/PostgreSQLDS`:

    <jta-data-source>java:jboss/datasources/PostgreSQLDS</jta-data-source>

Commit this change, and push.
