# Report Builder

--- 
[![Rust](https://github.com/singjc/report-builder/actions/workflows/rust.yml/badge.svg)](https://github.com/singjc/report-builder/actions/workflows/rust.yml)
[![Crates.io Version](https://img.shields.io/crates/v/report-builder)](https://crates.io/crates/report-builder)


This crate provides tools for generating HTML reports with interactive elements such as tables,
plots, and other visualizations. It's designed to be used as a library within other Rust projects.

## Features

- Create multi-section reports
- Add interactive tables with sorting, searching, and CSV export
- Include responsive Plotly charts
- Customizable styling and layout

## Usage

Add `report-builder` to your `Cargo.toml` dependencies:

```
[dependencies]
report-builder = "0.1.0"  # Replace with the latest version
```

Then, use the provided structs and methods to construct your report:

```
use report_builder::{Report, ReportSection};
use maud::html;
use plotly::Plot;

fn main() {
    let mut report = Report::new("MySoftware", "1.0", Some("logo.png"), "Analysis Report");
    
    let mut section = ReportSection::new("Results");
    section.add_content(html! { p { "This is a paragraph in the results section." } });
    
    // Add a plot (assuming you have a Plot object)
    let plot = Plot::new(); // Create and customize your plot
    section.add_plot(plot);
    
    report.add_section(section);
    report.save_to_file("report.html").unwrap();
}
```
