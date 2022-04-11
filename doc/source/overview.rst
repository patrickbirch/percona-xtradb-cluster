.. _overview:

============================================
Quick Start Guide for Percona XtraDB Cluster
============================================

This guide describes the procedure for setting up Percona XtraDB Cluster.

Examples provided in this guide assume there are three Percona XtraDB Cluster nodes, as a common choice for trying out and testing:

+--------+-----------+---------------+
| Node   | Host      | IP            |
+========+===========+===============+
| Node 1 | pxc1      | 192.168.70.61 |
+--------+-----------+---------------+
| Node 2 | pxc2      | 192.168.70.62 |
+--------+-----------+---------------+
| Node 3 | pxc3      | 192.168.70.63 |
+--------+-----------+---------------+

.. note:: Avoid creating a cluster with two or any even number of nodes,
   because this can lead to *split brain*.
   For more information, see :ref:`failover`.

The following procedure provides an overview
with links to details for every step:

1. :ref:`Install Percona XtraDB Cluster <install>` on all nodes
   and set up root access for them.

   It is recommended to install from official Percona repositories:

   * On Red Hat and CentOS, :ref:`install using YUM <yum>`.
   * On Debian and Ubuntu, :ref:`install using APT <apt>`.

#. :ref:`Configure all nodes <configure>` with relevant settings
   required for write-set replication.

   This includes path to the Galera library, location of other nodes, etc.

#. :ref:`Bootstrap the first node <bootstrap>` to initialize the cluster.

   This must be the node with your main database,
   which will be used as the data source for the cluster.

#. :ref:`Add other nodes <add-node>` to the cluster.

   Data on new nodes joining the cluster is overwritten
   in order to synchronize it with the cluster.

#. :ref:`Verify replication <verify>`.

   Although cluster initialization and node provisioning
   is performed automatically, it is a good idea to ensure
   that changes on one node actually replicate to other nodes.

#. :ref:`Install ProxySQL <load_balancing_with_proxysql>`.

   To complete the deployment of the cluster,
   a high-availability proxy is required.
   We recommend installing ProxySQL_ on client nodes
   for efficient workload management across the cluster
   without any changes to the applications that generate queries.

Percona Monitoring and Management
=================================

`Percona Monitoring and Management <https://www.percona.com/software/database-tools/percona-monitoring-and-management>`__ is the best choice for managing and monitoring Percona XtraDB Cluster performance.
It provides visibility for the cluster and enables efficient troubleshooting.

