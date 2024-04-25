# PACTs

### PACTs notes


### Consumer 

### Annotations:
- @Rule
- @Pact(consumer = "customer", provider = "retailer")
- @PactVerification(value = "retailer")
- @PactTestFor(pactMethod = "allProducts", port="9999")

### Producer

### Annotations:
- @Provider("ProductService")
- @PactBroker(url="http://localhost:9292",  authentication = @PactBrokerAuth(username = "pact_workshop", password = "pact_workshop"))
- @LocalServerPort
- @State("products exist")
- @Provider("retailer")
- @Consumer("customer")


Publish Pact from Consumer to Broker
mvn pact:publish





Misc(Consumer):
@SpringBootTest
@ExtendWith(PactConsumerTestExt.class)
@PactTestFor(providerName = "ProductService")

Misc(Producer):
@SpringBootTest(webEnvironment = RANDOM_PORT)
@IgnoreMissingStateChange
@TestTemplate
@ExtendWith(PactVerificationInvocationContextProvider.class)
