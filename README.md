# coursework
import streamlit as st 
import pandas as pd
import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt

import streamlit as st

# Set page configuration
st.set_page_config(
    page_title="Air Pollution ",
    page_icon=":bar_chart:",
    layout="wide",
    initial_sidebar_state="expanded"
)

# Custom CSS for styling
st.markdown("""
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f2f6;
        }
        .header-title {
            font-size: 36px;
            color: #333;
            text-align: center;
            padding: 20px;
            background-color: #fff;
            border-bottom: 2px solid #ccc;
        }
        .sidebar .sidebar-content {
            background-color: #fff;
            border-right: 2px solid #ccc;
        }
        .main .block-container {
            padding: 20px;
        }
        .footer {
            text-align: center;
            padding: 10px;
            background-color: #fff;
            border-top: 2px solid #ccc;
        }
    </style>
""", unsafe_allow_html=True)

# Main content
st.title('Air Pollution')



# Footer content
st.markdown('<div class="footer">Made By Zahra ❤️</div>', unsafe_allow_html=True)


# Enhance design with custom themes and responsive layout
st.markdown("<h1 style='text-align: center; color: blue;'>Air Pollution Analysis Dashboard</h1>", unsafe_allow_html=True)



# Import necessary libraries
import pandas as pd

# Define dummy data for demonstration
data = {
    'Parameter': ['Parameter 1', 'Parameter 2', 'Parameter 3'],
    'Value': [10, 20, 30],
    'Region': ['Region A', 'Region B', 'Region C']
}

# Create DataFrame
df = pd.DataFrame(data)

# Display the DataFrame
st.write(df)


# Improve navigation with sidebar menu
nav_choice = st.sidebar.radio("Navigation", ["Home", "Analysis", "About"])

if nav_choice == "Home":
    # Add content for the home page
    st.title("Welcome to Air Pollution Analysis Dashboard")
    st.write("This is the home page of the dashboard. Here you can find general information about air pollution analysis.")
elif nav_choice == "Analysis":
    # Add content for the analysis page
    st.title("Analysis Page")
    st.write("This page contains detailed analysis of air pollution data.")
    # Implement your analysis here
elif nav_choice == "About":
    # Add content for the about page
    st.title("About Page")
    st.write("This page provides information about the creators and purpose of this dashboard.")
    # Add about content here

# Add export functionality for downloading data
if st.button("Export Data"):
    df.to_csv("air_pollution_data.csv", index=False)
    st.success("Data exported successfully!")

















# Function to conduct linear regression analysis
def perform_linear_regression(X, y):
    slr = LinearRegression()
    slr.fit(X, y)
    return slr.coef_[0], slr.intercept_

# Function to display error margin report
def display_error_margin_report(title, analysis_results, code_snippet):
    st.header(title)
    st.write(analysis_results)
    st.code(code_snippet, language='python')

# Function to create a scatter plot
def create_scatter_plot(X, y, xlabel, ylabel, title):
    plt.figure(figsize=(8, 6))
    plt.scatter(X, y, color='blue')
    plt.xlabel(xlabel)
    plt.ylabel(ylabel)
    plt.title(title)
    plt.grid(True)
    st.pyplot()

# Function to create a regression line plot
def create_regression_line_plot(X, y, slope, intercept, xlabel, ylabel, title):
    plt.figure(figsize=(8, 6))
    plt.scatter(X, y, color='blue')
    plt.plot(X, slope * X + intercept, color='red')
    plt.xlabel(xlabel)
    plt.ylabel(ylabel)
    plt.title(title)
    plt.grid(True)
    st.pyplot()

def  display_options(title, analysis_results):
    st.header(title)
    st.write(analysis_results)


# Main function to define Streamlit app
def main():
    st.title('Air Pollution Analysis Dashboard')
    
    # Display introduction
    st.header("Introduction")
    st.write("Air pollution is a pressing global issue with significant implications for public health and the environment. The combustion of fossil fuels, industrial processes, and agricultural activities are primary sources of air pollutants such as particulate matter, nitrogen oxides, sulfur dioxide, and volatile organic compounds. These pollutants have adverse effects on human health, leading to respiratory diseases, cardiovascular problems, and even premature death. Moreover, air pollution contributes to environmental degradation, climate change, and biodiversity loss.")
    
    # Select analysis report
    report_options = [
        "Relevance of Analysis",
        "Study Reference",
        "Problem Statement",
        "Project Rationale",
        "Methodolgy",
        "Objective",

    ]
    selected_Option = st.selectbox('Select Option', report_options)

        # Display selected report
    if selected_Option == report_options[0]:
        display_options("Relevance of Analysis",
                        "Accurate assessment and understanding of air pollution are crucial for developing effective strategies to mitigate its impacts. Environmental agencies, policymakers, and researchers rely on comprehensive data analysis to identify pollution sources, evaluate trends, and formulate regulations to improve air quality. Additionally, businesses and industries are increasingly adopting sustainable practices to reduce their environmental footprint and comply with regulations, highlighting the importance of integrating environmental considerations into decision-making processes.")
    
    elif selected_Option == report_options[1]:
        display_options("Study Reference",
            "The study 'Health Impacts of Air Pollution' by Bingheng Chen & Haidong Kan (2007) provides valuable insights into the health effects of air pollution. Published in Environmental Health and Preventive Medicine, the study examines the correlation between air pollutant levels and various health outcomes, including respiratory and cardiovascular diseases. By quantifying the health burden associated with air pollution exposure, the study underscores the need for stringent emission control measures and public health interventions.")
    
    elif selected_Option == report_options[2]:
        display_options("Problem Statement",
            "Informed decision-making is severely hampered by the serious flaws in environmental impact assessments, such as their incompleteness, inaccuracy, and inefficiency, all of which are addressed in this work. Sustainability impact funds are unable to enable quick, well-informed judgements that strike a balance between financial objectives and environmental responsibilities due to their reliance on antiquated data, lack of comprehensive environmental measures, and labour-intensive procedures. Beyond these obstacles, the initiative aims to improve the strategic efficacy of investments and complement the goal of KORU IMPACT SOLUTIONS, which is to provide fund managers with accurate and useful environmental data. This project guarantees adherence to legal requirements while promoting genuine environmental stewardship.")
     
    elif selected_Option == report_options[3]:
        display_options("Project Rationale",
            "The project focuses on the ubiquitous problem of global air pollution in an effort to transform environmental impact reporting for KORU IMPACT SOLUTIONS. It suggests using extensive global databases to evaluate the financial and environmental effects of investments, especially with regard to air quality, and to automate and improve the process of creating impact reports. This research identifies crucial areas where air pollution is most detrimental and offers focused insights and mitigation techniques. This methodology surpasses conventional reporting techniques, which frequently fall short in providing the depth and urgency of data required for decision-making that is informed and sustainability-focused.")
    
    elif selected_Option == report_options[4]:
        display_options("Methodology",
                        "In the data pre-processing phase, we carefully evaluated our data sources relating to Greenhouse Gasses & Air Pollution, selecting relevant datasets and identifying quality issues like outliers, inaccuracies, missing or incomplete data, integration challenges, and duplicates. Every modification to the dataset, including cleaning, preparation, and integration steps, is documented to ensure accuracy and reliability. We employ visualizations, such as box plots and histograms, to illustrate data quality issues and their resolutions."
        "Data Pre-Processing:"
        "For instance, the Ozone Concentration dataset, spanning 1990 to 2015 across various countries, initially showed no missing values in key columns except for 7 missing entries in the 'Code' column, with no duplicates found. The dataset includes 1316 observations, with data collected consistently over the years for 188 entities. After addressing the missing 'Code' values, the dataset was fully cleaned, maintaining its original data count and distribution but with adjustments for completeness and accuracy. This cleaned dataset is now a reliable foundation for analyzing ozone concentration trends, demonstrating the importance of thorough data pre-processing for statistical analysis or modeling."
        "Data Pre-Processing:"
        "The next dataset examines air pollution mortality rates per 100,000 across countries from 1990 to 2019. Despite it being largely clean, it required removing 690 missing values to ensure accuracy. The cleaning process was streamlined by displaying only the initial rows post-clean-up for efficiency. Due to the dataset size, visual representation focused on highlighting general mortality trends over the 29 years, avoiding clutter by not detailing individual country data, thus offering a clear view of air pollution's global health impact."
        "Data Pre-Processing:"
       "The pre-processing phase of this dataset involved deduplication and missing data imputation, enhancing data reliability for global air quality trend insights. This meticulous approach not only streamlined visualization but also bolstered our research foundation, showcasing the dataset's enhanced usability for comprehensive environmental trend analysis."
        )
    elif selected_Option == report_options[5]:
        display_options("Objective",
                        "The objective is to create an innovative reporting framework that accurately assesses and elucidates the global influence of investments on air quality. This framework will offer practical strategies for reducing air pollution in the most affected areas, thus ensuring financial investments contribute positively to global sustainability targets. By achieving this, the project not only aims to rectify the current limitations of environmental impact assessments but also to foster a sustainable investment culture that prioritises environmental health alongside financial viability."
        )
                        

    # Dummy data for demonstration
    X = np.random.rand(100, 1) * 10
    y = 2 * X + np.random.randn(100, 1) * 2


    # Select analysis report
    report_options = [
        "Error Margin Report: Ozone Concentration vs. Sulphur Emissions",
        "Error Margin Report: Carbon Monoxide Emissions vs. Deaths",
        "Error Margin Report: Air Pollution Factors and Health Outcomes",
        "Error Margin Report: Comprehensive Analysis of Air Pollution's Impact on Health, Efficiency, and Society"
    ]
    selected_report = st.selectbox('Select Analysis Report', report_options)

    # Display selected report
    if selected_report == report_options[0]:
        display_error_margin_report(
            "Error Margin Report: Ozone Concentration vs. Sulphur Emissions", 
            "The regression analysis reveals a negative relationship between ozone concentration and sulphur emissions, indicating that higher ozone levels are associated with lower sulphur emissions",
            """from sklearn.linear_model import LinearRegression

X = air_emissions_df[['Ozone concentration-StateofGlobalAir']].values
y = air_emissions_df['SO₂ (Index)'].values

slr = LinearRegression()
slr.fit(X, y)
print('Slope: %.3f' % slr.coef_[0])
print('Intercept: %.3f' % slr.intercept_)"""
        )
        create_scatter_plot(X, y, 'Ozone Concentration', 'Sulphur Emissions', 'Scatter Plot: Ozone Concentration vs. Sulphur Emissions')
        slope, intercept = perform_linear_regression(X, y)
        create_regression_line_plot(X, y, slope, intercept, 'Ozone Concentration', 'Sulphur Emissions', 'Regression Line Plot: Ozone Concentration vs. Sulphur Emissions')
    elif selected_report == report_options[1]:
        display_error_margin_report(
            "Error Margin Report: Carbon Monoxide Emissions vs. Deaths",
            "The regression analysis provides insights into the potential relationship between carbon monoxide emissions and deaths. However, it's essential to interpret these findings cautiously and consider other factors that may influence mortality rates",
            """from sklearn.linear_model import LinearRegression
X = air_emissions_df[['Carbon Monoxide Emissions']].values
y = air_emissions_df['Deaths'].values

slr = LinearRegression()
slr.fit(X, y)
print('Slope: %.3f' % slr.coef_[0])
print('Intercept: %.3f' % slr.intercept_)"""
        )
    elif selected_report == report_options[2]:
        st.header(report_options[2])
        st.write("Error Margin Report: Air Pollution Factors and Health Outcomes",
            """The analysis reveals a positive correlation between air pollution levels and carbon intensity across various regions and economic sectors. Higher levels of air pollution, indicated by metrics such as particulate matter (PM2.5) concentration or nitrogen oxide (NOx) emissions, are associated with increased carbon intensity.

Regional variations are observed in the strength and nature of the relationship between air pollution and carbon intensity. For example, regions with heavy industrial activity or reliance on fossil fuels for energy production tend to exhibit higher carbon intensity levels relative to regions with cleaner energy sources or stringent environmental regulations.

The analysis further disaggregates data by economic sectors, such as manufacturing, transportation, and energy production. Results indicate that certain sectors, such as heavy industry and transportation, contribute disproportionately to both air pollution and carbon intensity, highlighting potential areas for targeted intervention and emissions reduction efforts.""")
    elif selected_report == report_options[3]:
        st.header(report_options[3])
        st.write("Error Margin Report: Comprehensive Analysis of Air Pollution's Impact on Health, Efficiency, and Society",
            """The regression analyses suggest that ozone concentration, sulphur dioxide levels, and particulate matter indices play significant roles in influencing mortality rates attributed to air pollution. These findings underscore the importance of implementing measures to mitigate air pollution and protect public health""",
            "Insert Python code snippet here"
        )
        # add overall anaylisi 

        st.header ("Analysis Oversight")
        st.write("  Our datasets, focusing on air pollution and greenhouse gases, underwent rigorous cleaning to remove duplicates and fill missing values, enhancing their reliability for analysis. We aim to use regression analysis to identify correlations within these datasets, understanding the impacts of air pollution and greenhouse gases on the environment, health, society, and global carbon footprint. This approach will provide insights into the complex dynamics between air quality and its broader implications, guiding informed decisions and strategies for mitigating adverse effects.")


        # Add conclusion
        st.header("Conclusion")
        st.write("In conclusion, the analysis presented in this report highlights the importance of understanding the complex relationship between air pollution and its impacts on public health and the environment. By leveraging data-driven approaches and advanced analytical techniques, stakeholders can make informed decisions to mitigate the adverse effects of air pollution and promote sustainable development. Moving forward, it is imperative to continue investing in research, technology, and policy initiatives aimed at addressing air quality issues and safeguarding the well-being of present and future generations.")
 
if __name__ == "__main__":
    main()
