# Apache Beam Workshop Instructor Repository
This repository contains useful tools to host a Beam Workshop based on the Mobile Gaming Example,
where a series of pipelines are developed to analyze data coming in from a bunch of players of
our imaginary mobile game.

Probably goes without saying, but you'll need Maven 3.3.1, the JDK, and git installed.

This repository contains utilities to:

* Start up a Spark cluster on Google Cloud Dataproc
* Start up a Flink cluster on Google Cloud Dataproc
* Start injecting data to a PubSub topic for streaming pipelines to subscribe to

## Setting up your environment
The `setup.sh` script will help you do all the setup that you will need for the workshop.
Run `source setup.sh -all` so you'll be able to check and set up all the necessary parameters,
including input files from GCS, output directories, default pubsub topic, GCP project, etc.

## Running the Injector

To start up an injector that sends data to the default PubSub topic, simply type `run-injector`
in your command line.

If you are looking to inject data to a plain text file, or to a Kafka topic, you will need to
run the Maven command directly. Look at the `run-injector` script for details.

## Apache Flink cluster in Google Cloud Dataproc

To start a Flink cluster in Dataproc, you need only run `start-flink`.

If you were able to add an allow-all rule to your firewall, you should be able to open the UI
from any computer:

    http://[IP for gaming-flink-m]:8088/

In the Flink UI, capture values of `jobmanager.rpc.address` (i.e. gaming-flink-w-5) and
`jobmanager.rpc.port` (i.e. 58268) in the Job Manager configuration, which should give you the
Job Manager node for the Flink cluster, which you can use to submit jobs through the Flink UI.


## Apache Spark cluster in Google Cloud Dataproc

To start a Flink cluster in Dataproc, you can run `start-spark`.

You can also check the Spark UI:

    http://[IP for gaming-spark-m]:18080/

For job submission, the `beam-workshop` repo contains commands to submit the job to
each of the clusters.
