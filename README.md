#here is the code writen by R to show the attribute of irises;



#here is the UI.R
library(shiny)
library(ggplot2)

dataset <- iris

shinyUI(pageWithSidebar(
  
  headerPanel("the attribute of irises"),
  sidebarPanel(
    
    selectInput('x', 'X', names(dataset)),
    selectInput('color', 'Color', (names(dataset)[5])),
    submitButton('Submit')
  ),
  
  mainPanel(
    plotOutput('plot')
  )
))
#here is the server.R
library(shiny)
library(ggplot2)

shinyServer(function(input, output) {
  
  output$plot <- reactivePlot(function() {
    
    ggplot(dataset, aes_string(x=input$x,color=input$color)) + geom_histogram()   
  }) 
})
