# Content

- [Load testing Report](https://github.com/shafinrahman912/BookingAppLoadTesting#load-testing-report)  
- [Summary](https://github.com/shafinrahman912/BookingAppLoadTesting#summary)  
- [Introduction](https://github.com/shafinrahman912/BookingAppLoadTesting#introduction)  
- [Install](https://github.com/shafinrahman912/BookingAppLoadTesting#install)      
- [Prerequisites](https://github.com/shafinrahman912/BookingAppLoadTesting#prerequisites)   
- [Elements of a Minimal Test Plan](https://github.com/shafinrahman912/BookingAppLoadTesting#prerequisites)    
- [Test Plan](https://github.com/shafinrahman912/BookingAppLoadTesting#test-plan)    
- [Collection of API](https://github.com/shafinrahman912/BookingAppLoadTesting#collection-of-api)   
    - [List of API](https://github.com/shafinrahman912/BookingAppLoadTesting#list-of-api) 
    - [Load the JMeter Script](https://github.com/shafinrahman912/BookingAppLoadTesting#load-the-jmeter-script)     
- [Make csv File](https://github.com/shafinrahman912/BookingAppLoadTesting#make-csv-file)    
- [Make jtl File](https://github.com/shafinrahman912/BookingAppLoadTesting#make-jtl-file)  
- [Make html File](https://github.com/shafinrahman912/BookingAppLoadTesting#make-html-file)  
- [HTML Report](https://github.com/shafinrahman912/BookingAppLoadTesting#html-report) 
- [Transaction Per Second](https://github.com/shafinrahman912/BookingAppLoadTesting#Transaction-Per-Second)    
- [Spike Testing](https://github.com/shafinrahman912/BookingAppLoadTesting#spike-testing)      
- [Endurance Testing](https://github.com/shafinrahman912/BookingAppLoadTesting#endurance-testing)
- [Read Test Data from CSV file in Jmeter](https://github.com/shafinrahman912/BookingAppLoadTesting#read-test-data-from-csv-file-in-jmeter)




# Load testing Report

| Concurrent Request  | Loop Count | Avg TPS for Total Samples  | Error Rate | Total Concurrent API request |
|               :---: |      :---: |                      :---: |                        :---: |      :---: |
| 1  | 1  | 1.98  | 0%      | 6  |
| 100  | 1  |  49.10     | 0%      | 600   |
| 500  | 1  |  238.45   | 0%   | 3000   |
| 1000  | 1  |  323.90  | 0%   | 6000   |
| 2000  | 1  |  313.52  | 0%   | 12000  |


### Summary
- Server can handle almost concurrent 424 API call with almost zero (0) error rate.



# Introduction

This document explains how to run a performance test with JMeter against a Booking Site.

# Install

**Java**  
https://www.oracle.com/java/technologies/downloads/

**JMeter**  
https://jmeter.apache.org/download_jmeter.cgi  

Click =>Binaries    
=>**apache-jmeter-5.6.2.zip**



# Prerequisites
- As of JMeter 4.0, Java 8 and above are supported.
- we suggest  multicore cpu's with 4 or more cores.
- Memory 16GB RAM is a good value.

# Elements of a minimal test plan
- Thread Group

    The root element of every test plan. Simulates the (concurrent) users and then run all requests. Each thread simulates a single user.

- HTTP Request Default (Configuration Element)

- HTTP Request (Sampler)

- Summary Report (Listener)

# Test Plan

Testplan > Add > Threads (Users) > Thread Group (this might vary dependent on the jMeter version you are using)

- Name: Users
- Number of Threads (users): 1, 100, 500, 1000, 2000
- Ramp-Up Period (in seconds): 10
- Loop Count: 1  

  1) The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

  2) All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

  3) Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

  4) The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.

# Collection of API




### List of API 

  - For creating Booking: [https://restful-booker.herokuapp.com/booking](https://restful-booker.herokuapp.com/booking)
  - For getting, updating, deleting  Booking: [https://restful-booker.herokuapp.com/booking/id](https://restful-booker.herokuapp.com/booking/1)


    
  ### Load the JMeter Script 
   - File > Open (CTRL + O)
   - Locate the "OPENCART_T1.jmx" file contained on this repo
   - Continue open OPENCART_T1 to OPENCART_T6
   - Open those file
   - The Test Plan will be loaded  
   
   ![testPlan](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/a3b9f91c-f772-4de0-b74e-5c20a4732cc4)


# Test execution (from GUI)
 
- JMeter should be initialized in GUI mode.
- Click on Run Button.</br>
![run](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/a16ed468-c6d3-401f-8d5f-fe11b7fa6f83)
- Check Different Types of Report.

    Summary and Aggregate  Report for  **Number of Threads 1 ; Ramp-Up Period 10s**
   
    Summary  Report           |  Aggregate  Report
    :-------------------------:|:-------------------------:
    ![BookingApp_t1_summary](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/7494e916-6501-4688-b152-4bf31285cb78)  |  ![BookingApp_t1_agg](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/13846ce9-41b0-4f20-898d-c63b3ed312d6)

    Aggregate  Report for  **Number of Threads 2000 ; Ramp-Up Period 10s**
    Aggregate  Report
    :-------------------------:|
    ![BookingApp_t2000_summary](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/8b23ae4c-5bd2-4517-9494-2cda58172c42)


# Test execution (from the Terminal)
 
- JMeter should be initialized in non-GUI mode.
- Make a report folder in the **bin** folder.  
- Run Command in __jmeter\bin__ folder. 

 ### Make csv file    
 
   - **n**: non GUI mode
  - **t**: test plan to execute
  - **l**: output file with results   

```bash
  jmeter -n -t  BookingApp_csv_dataset_t1.jmx -l BookingAppLoadTesting\report\BookingApp_csv_dataset_t1.csv
```   
![BookingApp_t1_csv](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/0019e4cc-a1fa-45ed-a39c-93e6ddb4a44d)


 ### Make jtl file

```bash
  jmeter -n -t  BookingApp_csv_dataset_t1.jmx -l BookingAppLoadTesting\report\BookingApp_csv_dataset_t1.jtl
```      
  Then continue to upgrade Threads( 1, 100, 500, 1000, 2000 ) by keeping Ramp-up-Period Same.   
   
  ![BookingApp_t1_jtl](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/8bd2813d-eef9-4f0e-8b89-8897d62d93fd)
  ![BookingApp_allJTLs](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/4d4f6056-367e-44ca-bf3d-5da384100aec)

  After completing this command  

 ### Make html file   
  
  ```bash
  jmeter -g BookingAppLoadTesting\report\BookingApp_csv_dataset_t1.jtl -o BookingAppLoadTesting\report\BookingApp_csv_dataset_t1.html
```
 

  - **g**: jtl results file

  - **o**: path to output folder

  ![BookingApp_t1_csv_cmd](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/62f250a8-ea72-4670-8de0-71484ac3e998)
  ![BookingApp_reports](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/3595c8c8-fa1e-4e13-b10e-a5e124d22db4)

# HTML Report

**Number of Threads 1 ; Ramp-Up Period: 10s**
   
Requests Summary             |  Statistics
:-------------------------:|:-------------------------:
![BookingApp_t1_100pass](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/f9c72ff1-fc0a-4ad2-a18b-9cc0f594d905)  |  ![BookingApp_t1_stats](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/72d2eaf5-36f6-4602-93c0-9f3ca857b45f)



**Number of Threads 100 ; Ramp-Up Period 10s**
   
Requests Summary             |  Statistics
:-------------------------:|:-------------------------:
![BookingApp_t1_100pass](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/f9c72ff1-fc0a-4ad2-a18b-9cc0f594d905)  |  ![BookingApp_t100_stats](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/6a528423-6c94-49c1-90fb-206d5a56a517)


**Number of Threads 500 ; Ramp-Up Period 10s**
   
Requests Summary             |  Statistics
:-------------------------:|:-------------------------:
![BookingApp_t1_100pass](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/f9c72ff1-fc0a-4ad2-a18b-9cc0f594d905)  |  ![BookingApp_t500_stats](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/2db8d826-1653-4c49-83a8-68fda7a16ce9)


**Number of Threads 1000 ; Ramp-Up Period 10s**
   
Requests Summary             |  Statistics
:-------------------------:|:-------------------------:
![BookingApp_t1_100pass](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/f9c72ff1-fc0a-4ad2-a18b-9cc0f594d905)  |  ![BookingApp_t1000_stats](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/e9536cde-4f0a-46bb-ac5e-9ddcc5cf3926)


**Number of Threads 2000 ; Ramp-Up Period 10s**
   
Requests Summary             |  Statistics
:-------------------------:|:-------------------------:
![BookingApp_t1_100pass](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/f9c72ff1-fc0a-4ad2-a18b-9cc0f594d905)  |  ![BookingApp_t2000_stats](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/685bed04-ecd3-4cbd-bc60-1706faf2acb6)


# Transaction Per Second

Transaction Per Second **Number of Threads 2000 ; Ramp-Up Period 10s**
   
![BookingApp_t2000_tps](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/5bbcbed4-5796-4b4c-8807-a312126a9b80)



# Read Test Data from CSV file in Jmeter    

- Create a CSV file in the test suite folder and add test data to it.  <br/>
![createCSV](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/f9f5da35-7d07-46c7-9911-a7e80d3c68f9)

- Add a Config Element CSV Data Set Config in Jmeter.   <br/>

![configCSV](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/82972a24-c3e8-42fb-84c2-f26ba41014fa)


- Configure ' CSV Data Set Config ' based on the need such as providing path of CSV file and variable names and other configs.   <br/>

![readCSV](https://github.com/shafinrahman912/BookingAppLoadTesting/assets/83553368/a64c69b2-280b-468a-8a3f-bf7db0bfb7c0)

- Run the test to see if data from the CSV file is read and populated in the results.  <br/>

- Run the test to see if data from CSV file is read and populated in the results.    <br/>  




