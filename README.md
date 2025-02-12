# PySpark and Apache Spark Learning Repository

This repository documents my hands-on learning journey and projects involving **Apache Spark**, **PySpark**, and **Delta Lake**. The topics covered span from the basics of distributed computing to advanced data engineering practices. Each section includes explanations of core concepts, practical implementations, and optimization techniques for efficient big data processing.

## Topics Covered

### 1. **Apache Spark vs Hadoop MapReduce**
   - **Overview**: Apache Spark and Hadoop MapReduce are both frameworks used for big data processing, but they differ significantly in performance, scalability, and ease of use. 
     - **Performance**: Spark processes data in memory, allowing for much faster computation compared to Hadoop MapReduce, which writes intermediate data to disk. Spark’s ability to cache and hold data in memory significantly reduces processing time.
     - **Scalability**: Spark can scale more efficiently in both horizontal and vertical contexts due to its distributed architecture and efficient cluster management.
     - **Ease of Use**: Spark provides high-level APIs (like DataFrame and SQL) which are much easier to work with compared to the low-level MapReduce API.

### 2. **PySpark Structured Streaming**
   - **Overview**: Structured Streaming in PySpark allows for the processing of real-time data streams. It enables building scalable, fault-tolerant applications that can continuously process incoming data from sources such as Kafka, files, and sockets.
   - **Key Features**:
     - **Declarative API**: Allows you to specify your streaming computation as a DataFrame or SQL query, making it easier to express and optimize.
     - **Fault Tolerance**: Ensures that the stream processing is resilient to node failures.
     - **Exactly Once Semantics**: Guarantees that each record is processed once and only once.

### 3. **Window Functions in PySpark**
   - **Overview**: Window functions allow for the analysis of data within a specific window of rows in the DataFrame. They are useful for operations like calculating moving averages, cumulative sums, and ranking.
   - **Example**: Using a window function to calculate a rolling average of sales data over the last 7 days.
   - **Key Concepts**: Partitioning and ordering of data are crucial for window functions to work correctly, ensuring the right subset of data is used for each calculation.

### 4. **Date Functions in PySpark**
   - **Overview**: PySpark provides a set of built-in functions to handle date and time-related operations such as date differences, date formatting, and extracting date parts.
     - **Key Functions**:
       - `current_date()`: Returns the current date.
       - `datediff()`: Returns the difference between two dates.
       - `date_format()`: Formats the date as a string.
   - **Use Case**: Performing time-based transformations, such as filtering data for a specific date range or calculating time-based metrics.

### 5. **Array Functions in PySpark**
   - **Overview**: PySpark provides various array functions to manipulate and process arrays within DataFrames. These functions allow for tasks like finding the maximum value in an array, checking if an array contains a certain element, and merging multiple arrays.
   - **Common Functions**:
     - `array_contains()`: Checks if an array contains a specific element.
     - `array_distinct()`: Returns an array with distinct elements.

### 6. **PySpark Advanced Level Interview Questions**
   - **Overview**: This section compiles a set of advanced interview questions that test deep understanding of PySpark’s capabilities, including its architecture, performance optimization techniques, and real-world problem-solving using Spark’s distributed framework.
   - **Topics**:
     - Performance optimizations in Spark.
     - Understanding the execution plans (logical vs physical plans).
     - Differences between `RDD`, `DataFrame`, and `Dataset` in terms of usage and optimization.

### 7. **Spark Context**
   - **Overview**: **SparkContext** is the entry point for Spark functionality. It allows the driver program to connect to the Spark cluster and manage distributed data processing tasks.
   - **Role**: Manages the **Job** and **Task** scheduling. Also facilitates data distribution and fault tolerance in a cluster environment.
   - **Initialization**: SparkContext needs to be initialized before running any Spark operations, and it is responsible for connecting to the cluster manager.

### 8. **Spark Architecture**
   - **Overview**: Spark's architecture consists of several key components that work together to process distributed data:
     - **Driver**: The main process that runs the Spark application and coordinates work.
     - **Executor**: A worker node in the cluster responsible for executing tasks.
     - **Task**: A unit of work sent to the executor.
     - **Cluster Manager**: Manages the resources of the cluster (e.g., YARN, Mesos, Kubernetes).
     - **DAG (Directed Acyclic Graph)**: Represents the computation as a series of stages, allowing Spark to optimize execution.

### 9. **Slowly Changing Dimension Using PySpark**
   - **Overview**: Slowly Changing Dimensions (SCD) are common in data warehousing where the dimensional data changes over time. Implementing SCD in PySpark involves handling records that change, stay the same, or are inserted as new records.
   - **Techniques**:
     - SCD Type 1: Overwrites the old data with the new one.
     - SCD Type 2: Tracks historical changes by adding new records with the updated data.
     - SCD Type 3: Stores the previous value alongside the current value.

### 10. **Data Ingestion Using InferSchema**
   - **Overview**: In PySpark, `inferSchema` automatically detects and assigns the correct data types to columns when reading data. This feature is particularly useful when working with semi-structured data such as CSV or JSON where the schema is not predefined.
   - **Performance Considerations**: While `inferSchema` is convenient, it can be slow for large datasets, so using predefined schemas might be more efficient in production environments.

### 11. **Data Reading with PySpark**
   - **Overview**: PySpark supports reading various file formats, such as **CSV**, **JSON**, **Parquet**, and **ORC**. It provides a flexible API to read structured and semi-structured data into DataFrames for further processing.
     - **Best Practices**: When reading large datasets, it's best to read data in parallel across multiple nodes in a cluster.

### 12. **RDD vs DataFrame vs Dataset**
   - **Overview**: Spark provides three core abstractions: 
     - **RDD**: A low-level abstraction that provides fine-grained control over the data and operations.
     - **DataFrame**: A higher-level abstraction that optimizes performance with the Catalyst optimizer. It’s similar to a table in a relational database.
     - **Dataset**: Provides the benefits of both RDDs and DataFrames, offering a type-safe, object-oriented API.

### 13. **PySpark Query Optimization**
   - **Overview**: Spark's **Catalyst Optimizer** automatically optimizes queries. This section covers how Spark optimizes query execution using techniques such as **predicate pushdown**, **filter pushdown**, and **join optimizations**.
   - **Performance Tuning**: Techniques to improve query execution times, such as caching data in memory, partitioning data correctly, and using appropriate join strategies.

### 14. **Logical Plan vs Physical Plan**
   - **Overview**: Spark uses two types of plans for query execution:
     - **Logical Plan**: Represents the query in an abstract form, detailing the logical operations to be performed.
     - **Physical Plan**: The optimized version of the logical plan that includes the actual execution strategies, such as the order of operations and partitioning strategies.

### 15. **Spark Session**
   - **Overview**: A **SparkSession** is the unified entry point for working with DataFrames and SQL. It encapsulates SparkContext, SQLContext, and HiveContext, simplifying the creation and management of Spark applications.
   - **Usage**: Creating a session is as simple as:
     ```python
     spark = SparkSession.builder.appName("SparkApp").getOrCreate()
     ```

### 16. **Narrow vs Wide Transformations**
   - **Overview**: In Spark, transformations are classified as **narrow** or **wide**:
     - **Narrow transformations**: Operations where each input partition contributes to a single output partition (e.g., map, filter). These are generally more efficient.
     - **Wide transformations**: Operations that require data shuffling between partitions (e.g., groupBy, join). These can lead to significant performance bottlenecks.

### 17. **Coalesce() vs Repartition()**
   - **Overview**: Both **coalesce()** and **repartition()** are used to change the number of partitions in a DataFrame.
     - **Coalesce()** is more efficient when reducing the number of partitions because it avoids a full shuffle of the data.
     - **Repartition()** performs a full shuffle and is generally used to increase the number of partitions for parallelism.

### 18. **Cache() vs Persist()**
   - **Overview**: **Cache()** and **Persist()** are used to store intermediate data in memory. `Cache()` is a shorthand for `persist(MEMORY_AND_DISK)`, while `Persist()` allows you to specify different storage levels (e.g., **MEMORY_ONLY**, **DISK_ONLY**).
   - **Use Case**: Cache results of computations that are reused multiple times to avoid re-computing.

### 19. **Importance of Partitions in PySpark**
   - **Overview**: Data is divided into **partitions** in Spark for parallel processing. Understanding the importance of partitioning is critical for optimizing performance in distributed systems.
   - **Best Practices**: Proper partitioning allows Spark to distribute work evenly across the cluster and minimizes data shuffling.

### 20. **Broadcast Variables**
   - **Overview**: Broadcast variables are used to efficiently distribute a large read-only variable to all nodes in the cluster. This helps in minimizing the amount of data sent over the network, particularly in join operations.
   - **Use Case**: Broadcasting a small lookup table across all nodes to join with a larger dataset.

### 21. **df.show() vs df.collect()**
   - **Overview**: The `show()` function is used to display a sample of the DataFrame to the console, while `collect()` returns the entire DataFrame as a list of Rows to the driver. It is important to use `collect()` cautiously, especially when dealing with large datasets, as it may cause memory issues.

### 22. **Lazy Evaluation**
   - **Overview**: Spark uses **lazy evaluation** to delay the execution of data transformations until an action (e.g., `collect()`, `show()`) is triggered. This allows Spark to optimize the execution plan by grouping multiple operations together.

### 23. **Optimizations in Delta Lake**
   - **Overview**: Delta Lake offers several optimizations to improve the performance of data lakes, including:
     - **Z-Order**: Optimizing data for read queries by colocating related data.
     - **Clustering**: Organizing data into smaller partitions for faster query performance.
     - **Time Travel**: Querying previous versions of data for audit or analysis purposes.

### 24. **Handling Skewed Data in PySpark**
   - **Overview**: Skewed data occurs when some partitions are much larger than others, which can lead to inefficient processing. Techniques like **salting** (adding random prefixes to keys) and **broadcast joins** help to mitigate the impact of skewed data.

### 25. **Broadcast Join**
   - **Overview**: A **broadcast join** is a type of join where the smaller DataFrame is broadcasted to all nodes, which helps in reducing shuffle costs when joining large and small datasets.

### 26. **Spill in Spark**
   - **Overview**: **Spill** occurs when the data exceeds the available memory and is written to disk. This can significantly slow down the performance of Spark jobs. Optimizing partition sizes and tuning memory configurations can help prevent spills.

### 27. **Delta Lake Time Travel**
   - **Overview**: Delta Lake allows you to query older versions of the data using **time travel**. This feature enables users to access data as it existed at a particular timestamp or version.

---

This repository is a comprehensive guide for understanding and working with Apache Spark and Delta Lake. It serves as a helpful reference for anyone looking to deepen their knowledge of these powerful big data tools.

---

Let me know if this helps or if you would like to add further details to any section!

## Link to Refer :-https://www.youtube.com/watch?v=fOCiis31Ng4&t=5s
