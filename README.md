# What is Cloud Food Store?
Cloud Food Store is a solution based on a microservice architecture that solves the problem of small and medium-sized companies selling products (and not only) to find customers. The service provides an opportunity to create your own product database and accept orders, the seller is required to accept payments and deliver. Thus, the service serves as a distributor of information about the product base for companies.

## How does the buyer and seller interact?
Before the first buyers appear, the company needs to place the first products. To do this, either json is uploaded to the site API, or one product is added to the system at a time using the built-in system. Let's assume that the work is finished. The buyer visits the website, goes through the registration procedure, selects the product that meets his requirements, adds the right amount to the cart. Then, if desired, carries out the order. At this point, the company receives all possible contact information and the buyer's address. The company must agree on the delivery time and payment method or other conditions for receiving the goods (in fact, CFS can do much more, you can change the name and even sell computer games). Obviously, then the client receives the goods, after that he has the right to evaluate the quality of the services and goods provided on the site and evaluate the company and change the overall rating that all users see. This is how trading takes place on Cloud Food Store.

## Overview
An important feature of the series of services is that they will be able to fully work only in Docker. It was originally planned that it would work in this environment, as a result of convenience and portability.
The services work each on their own port:
1. CFS (The core of the user part of the project.) - 3939, by accessing this port, you get access to the API.
2. CFSClient (A website where users can place orders and search the store.) - 4040, to access the API, you need to add "/api" here.
3. ShopOwnerSide (The core part of the companies' service.) - 15676, by accessing this port, you get access to the API.
4. ShopOwnerSite (A website to simplify the work of companies.) - 9191, to access the API, you need to add "/api" here.
5. TelegramBotCFS (A bot that gives basic information about purchases and orders.) - 1515, by accessing this port, you get access to the API. To use bot go to http://t.me/ohwetouhweth_bot.

## How to launch it?
1. The first step is to create a separate network in docker: "docker network create shared-network", it is needed to connect containers to each other for data exchange.
2. Further we recommend using IntelliJ IDEA for this. All you have to do is clone any module from this repository via github clone in the IDE. You need to open in IDE git -> clone -> paste in URL the repository of modules that you want to connect to the system.
3. Then go to the Maven compiler and select swagger-spring/Lifecycle and use "package", a "jar" file will be created. 
4. Then you run the docker-compose file, which will do the rest of the work on packaging the service for you. This way you can start all the services in turn.
5. **Important! This procedure (2-4 steps) must be performed for each module that is specified in this repository separately.**

## FAQ
1. How does the owner of the marketplace receive income?
- To register a company, a confirmation is required. It is assumed that the one who will launch the marketplace will explain where to send money and will send requests for approval of companies that have passed confirmation.

2. Why can't I log in from the company after registration?
- The company has not confirmed the payment, you need to confirm the company by email via ShopOwnerSide.

3. Is it necessary to run all services?
- No, for minimal performance, CFS and ShopOwnerSide are required - this will allow the service to work using json requests. In order for users to work through the site, you also need to launch CFSClient and ShopOwnerSite to these services.

## The authors of the project
There is only one author - the creator of this repository, Evgeny Ivanov.
